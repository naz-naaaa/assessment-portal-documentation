# Assessment Portal — Tech Stack

**Status:** Proposed v0.1
**Date:** 2026-08-14
**Scope:** Recommendation for Phase 1 (MVP) per `requirements.md` §12, with notes on what changes in later phases.

---

## 1. Guiding principles

- **One deployable app.** Backend and frontend live in the same repo *and* the same runtime — no separate API service to stand up, version, and deploy in lockstep.
- **Boring, proven technology.** This is an internal tool for ~50 concurrent users, not a scaled consumer product. Every piece below is chosen because a small team can run it without a platform/ops function.
- **Build for Phase 1 only.** Phase 2/3 items from the requirements doc (code-exec sandboxing, HRIS, Slack, certificates) are named but deliberately not built into the initial architecture — adding them later should mean *adding a piece*, not rewriting.
- **Optimize for one or two engineers owning this end to end**, in the spirit of a forward-deployed setup: fast iteration, minimal infra ceremony, easy to hand off or extend.

## 2. Recommended stack

| Layer | Choice | Why |
|---|---|---|
| Language | TypeScript (frontend + backend) | One language, one type system, shared types between UI and server code — no schema drift between a separate API and client. |
| Framework | **Next.js (App Router)** | Gives you frontend (React) and backend (Server Actions / Route Handlers) in one codebase and one deploy. This *is* the monorepo — no workspace tooling needed to get backend+frontend together. |
| Database | **PostgreSQL** | Relational fits the data model in requirements.md §9 directly (Users, Tracks, Assessments, Attempts, AuditLog — all relational with clear FKs). Managed instance (RDS / Neon / Supabase) rather than self-hosted. |
| ORM | **Prisma** | Schema-first, type-safe queries, built-in migrations — maps 1:1 onto the §9 data model and keeps DB schema in the repo as code. |
| Auth | **Auth.js (NextAuth)** | Handles Google Workspace / Microsoft SSO (FR-1) and email+password fallback out of the box. Session/JWT callbacks are enough to carry role (Admin/Reviewer/Candidate/Super Admin) for RBAC (FR-2) without a separate identity service. |
| UI | **Tailwind CSS + shadcn/ui** | Accessible-by-default components (helps with NFR-5 WCAG 2.1 AA) without hand-building a design system. |
| File storage | S3-compatible bucket (AWS S3 or Cloudflare R2) | Needed for file-upload question type (FR-5) and any exported reports (FR-30). |
| Email | **Resend** (or SES if already on AWS) | Transactional email for FR-31 notifications. Small API, no queue infra required at this volume. |
| Scheduled jobs | Platform cron (Vercel Cron) or a single `node-cron` process | Due-date reminders (FR-14) and digest notifications. No message queue (Redis/BullMQ) needed at 50 concurrent users — add one later only if job volume actually demands it. |
| Testing | **Vitest** (unit) + **Playwright** (e2e for take-assessment / grade / sign-off flows) | Matches Next.js tooling, minimal config. |
| Hosting | Single container or Vercel, deployed to whatever cloud zevonai.com already runs on (per requirements.md §7 — confirm) | Avoids standing up new infra just for this tool. |
| CI | GitHub Actions: lint → typecheck → test → deploy | Nothing bespoke. |
| Package manager | pnpm | Faster installs, fine for a single-app repo. |
| AI / LLM provider | **Mistral AI** (chat/completion API) | Parses an admin-uploaded PDF question bank into structured question/option/answer-key JSON for the assessment builder (extends FR-5). Extraction result is always shown in an editable preview — nothing persists until the admin confirms. Company-provided API key. |

## 3. Repo layout

Because Next.js unifies backend and frontend, the "monorepo" is really just one app — no Turborepo/Nx/workspaces needed for Phase 1:

```
assessment-portal/
├── app/
│   ├── (candidate)/       # dashboard, take-assessment flow
│   ├── (reviewer)/        # grading queue
│   ├── (admin)/           # assessment authoring, tracks, reporting
│   └── api/               # route handlers (webhooks, exports, etc.)
├── components/            # shared UI
├── lib/
│   ├── auth.ts            # Auth.js config + role helpers
│   ├── db.ts              # Prisma client
│   ├── grading.ts         # auto-grading logic (MCQ/single-choice)
│   └── audit.ts           # audit log writer (FR-34)
├── prisma/
│   ├── schema.prisma
│   └── migrations/
├── tests/
└── package.json
```

If a genuinely separate service is needed later (see §5), it becomes a sibling folder (e.g. `code-runner/`) and pnpm workspaces get introduced *at that point* — not preemptively.

## 4. AI-assisted PDF question import

Admins can upload a PDF of questions (extends the manual question builder from FR-5) instead of entering everything by hand:

1. Extract raw text from the uploaded PDF server-side (e.g. `pdf-parse`).
2. Send the text to **Mistral AI**'s completion API with a structured-output prompt, returning candidate questions/options/answer-keys as JSON.
3. Render the result in the same question-builder UI as an **editable preview** — every field is a normal form field the admin can correct. Nothing is written to the database until the admin explicitly saves.

**API key handling:** the Mistral API key is company-provided and must be admin-configurable at runtime (not a static env var needing a redeploy to rotate).

- New `Integration` (or `SystemSetting`) table holds the key, **encrypted at rest** (AES-256-GCM, encryption key from a server-only env var — never the API key itself in plaintext in the DB).
- Decrypted only server-side, at the point of calling Mistral; never returned to the client. The settings UI shows a masked value (e.g. `sk-••••1234`) after save, never the full key.
- Per requirements.md §4, **Super Admin** owns "integrations" — the key-configuration screen is Super Admin-scoped; Admins can still use the PDF-import feature itself.
- Saving/rotating/removing the key is an audited action (FR-34/NFR-8: actor + timestamp).

## 5. Deliberately excluded from v1 (avoid over-engineering)

| Not doing now | Why | Revisit when |
|---|---|---|
| Microservices / separate API service | Adds deploy coordination and network calls for no benefit at this scale. | If a second consumer of the API shows up (e.g. mobile app, HRIS pulling data directly). |
| GraphQL | REST-ish route handlers / server actions are enough for a handful of internal screens. | Only if the frontend needs highly flexible querying across many clients — unlikely here. |
| Sandboxed code execution service (Judge0/Piston/custom) | Requirements doc explicitly defers auto-graded code exercises to Phase 2 (§11 Q6, §12). Building it now is scope creep. | Phase 2, once it's confirmed coding questions need auto-grading rather than manual review. |
| Message queue (Redis/BullMQ/SQS) | Notification and reminder volume at 50 concurrent users doesn't need one. | If email/notification volume or job complexity grows materially. |
| Kubernetes / container orchestration | One container, one database — no orchestration problem to solve yet. | If multi-service architecture actually emerges (see microservices row). |
| Multi-tenant architecture | Requirements doc confirms single-tenant, internal-only (§7). | Not anticipated — flag if that assumption changes. |

## 6. Open items that affect this recommendation

These map to open questions in `requirements.md` §11 — confirm before locking the stack in:

- **SSO provider (Google vs. Microsoft)** — Auth.js supports both; just needs the actual choice to configure the right provider.
- **Existing cloud provider for zevonai.com** — determines managed Postgres choice (RDS if AWS, Neon/Supabase if provider-agnostic) and hosting target.
- **Code-exercise auto-grading requirement** — confirms whether §4's sandbox line item is really Phase 2 or needs pulling into v1.
