# Assessment Portal — Requirements Document

**Project:** Onboarding Assessment Portal
**Organization:** Zevon AI (zevonai.com)
**Status:** Draft v0.1
**Date:** 2026-08-14

> This is a first-draft requirements document based on Zevon AI's public profile (AI-driven ed-tech platform offering tech courses, mentorship, and cybersecurity training) plus standard patterns for staff onboarding/assessment tools. Assumptions are called out explicitly in §11 — please confirm or correct them before build starts.

---

## 1. Overview

Zevon AI needs an internal **Assessment Portal** to evaluate new staff during onboarding — verifying role-relevant skills (e.g. technical, cybersecurity, mentorship/teaching ability, support), tracking onboarding completion, and giving HR/managers a single place to review results before a new hire is signed off as fully onboarded.

## 2. Purpose & Goals

- Standardize how new staff are assessed during onboarding, replacing ad-hoc spreadsheets/emails/interviews.
- Give HR and hiring managers visibility into who has completed which onboarding assessments and how they scored.
- Support multiple assessment types relevant to Zevon AI's business: multiple-choice/knowledge checks, coding/technical exercises, and manually-graded practical tasks.
- Produce an auditable record of onboarding sign-off per employee.

## 3. Scope

### In scope
- Internal-only portal (staff/employees), not the public student-facing course platform.
- Assessment authoring, delivery, auto-grading (where possible), manual review/grading, and reporting.
- Onboarding checklist/workflow tracking tied to assessment completion.
- Role-based access for Admin (HR/L&D), Reviewer (manager/team lead), and Candidate (new hire).

### Out of scope (v1)
- Public student-facing courses/certificates on zevonai.com (separate system).
- Payroll, benefits, or other HRIS functions.
- Video-proctoring / anti-cheating beyond basic tab-switch/time tracking.
- Native mobile apps (web-responsive only).

## 4. Stakeholders & User Roles

| Role | Description | Key needs |
|---|---|---|
| **Admin (HR / L&D)** | Owns onboarding programs and portal configuration | Create/edit assessments, assign to hires, manage users/roles, view all results |
| **Reviewer (Manager / Team Lead)** | Oversees onboarding of their direct reports | View/grade assigned team's submissions, sign off onboarding |
| **Candidate (New Hire / Staff)** | Person completing onboarding | Take assessments, view own progress/results, resume in-progress attempts |
| **Super Admin (IT/Ops)** | Technical owner | User provisioning, integrations, audit logs |

## 5. Functional Requirements

### 5.1 Authentication & Access
- FR-1: Users log in via company SSO (Google Workspace / Microsoft, TBD) or email+password with invite-only registration.
- FR-2: Role-based access control (Admin, Reviewer, Candidate, Super Admin).
- FR-3: New hires are provisioned an account automatically when added to an onboarding cohort (manual entry or CSV import in v1).
- FR-4: Session timeout and secure password/reset flow if not fully SSO-based.

### 5.2 Assessment Management (Admin)
- FR-5: Admin can create assessments composed of multiple question types: multiple-choice, single-choice, short answer, code exercise, file upload, and free-text (manually graded).
- FR-6: Admin can group questions into a reusable **question bank**, tagged by skill/role/topic.
- FR-7: Admin can set per-assessment rules: time limit, pass threshold, number of attempts allowed, randomize question order, question pool (random subset from bank).
- FR-8: Admin can assign an assessment to a role/department template (e.g. "Cybersecurity Instructor Onboarding", "Support Staff Onboarding") so it's auto-applied to new hires in that track.
- FR-9: Admin can preview an assessment as a candidate would see it before publishing.
- FR-10: Admin can archive/version assessments without breaking historical results.

### 5.3 Onboarding Workflow
- FR-11: Each new hire is assigned an **onboarding track** = ordered list of assessments/tasks with due dates.
- FR-12: Track progress is visible as a checklist/progress bar (Not started / In progress / Submitted / Passed / Failed / Needs review).
- FR-13: Reviewer/Admin can manually mark a non-assessment onboarding step complete (e.g. "signed NDA") for a unified checklist view.
- FR-14: Automatic reminder when a due date is approaching or passed (see 5.8).
- FR-15: Final "onboarding complete" status requires all required assessments to be passed and/or reviewer sign-off.

### 5.4 Test-Taking Experience (Candidate)
- FR-16: Candidate sees a dashboard of assigned assessments with status and due dates.
- FR-17: Candidate can start an assessment, see instructions, time remaining (if timed), and question progress.
- FR-18: Auto-save of answers periodically and on navigation, so a lost connection doesn't lose progress.
- FR-19: Candidate can resume an in-progress attempt within the allowed window; attempt auto-submits when time expires.
- FR-20: Candidate sees their results/feedback once released (immediately for auto-graded, after review for manually graded).
- FR-21: Basic integrity measures: disable copy/paste on code questions (configurable), log tab-switch/focus-loss events, timestamp submissions.

### 5.5 Grading & Scoring
- FR-22: Objective question types (MCQ, single-choice) auto-graded on submission.
- FR-23: Code exercises auto-graded via test cases where feasible (e.g. run against expected input/output), with manual override available.
- FR-24: Free-text/file-upload questions routed to Reviewer queue for manual grading with a rubric/comment field.
- FR-25: Overall score computed per assessment; pass/fail determined against configured threshold.
- FR-26: Reviewers can leave per-question and overall feedback visible to the candidate (configurable).

### 5.6 Reporting & Analytics
- FR-27: Admin dashboard: onboarding funnel across all active hires (started, in progress, completed, overdue).
- FR-28: Per-hire report: all assessment attempts, scores, time spent, reviewer comments.
- FR-29: Per-assessment analytics: average score, pass rate, question-level difficulty (% correct), time distribution — to help Admin improve question quality.
- FR-30: Export results to CSV/PDF.

### 5.7 Notifications
- FR-31: Email notifications for: assessment assigned, due-date reminder, submission received, results released, onboarding complete.
- FR-32: In-app notification center for pending actions (e.g. reviewer has ungraded submissions).

### 5.8 Admin/User Management
- FR-33: Super Admin manages user accounts, roles, and department/track assignment.
- FR-34: Audit log of key actions (assessment published, grade changed, account role changed).

## 6. Non-Functional Requirements

- **NFR-1 Security:** All traffic over HTTPS; passwords hashed (bcrypt/argon2) if not fully SSO; role-based authorization enforced server-side on every endpoint; no PII in logs.
- **NFR-2 Privacy:** Candidate assessment data accessible only to that candidate, their assigned Reviewer(s), and Admins — not other candidates or unrelated staff.
- **NFR-3 Performance:** Assessment pages (question load, autosave) respond within 1–2s under normal load; supports at least 50 concurrent test-takers for v1.
- **NFR-4 Availability:** Target 99.5% uptime during business hours; graceful handling of dropped connections during an active attempt (no lost answers).
- **NFR-5 Accessibility:** WCAG 2.1 AA for core flows (keyboard navigation, screen-reader labels, sufficient contrast).
- **NFR-6 Browser support:** Latest 2 versions of Chrome, Edge, Firefox, Safari; responsive down to tablet width (desktop-first, since coding questions need a real keyboard).
- **NFR-7 Data retention:** Assessment results retained per company HR record-keeping policy (default: duration of employment + N years — confirm with HR/Legal).
- **NFR-8 Auditability:** Grade changes and role changes are logged with actor and timestamp.

## 7. System Architecture Assumptions

- Web application: browser-based frontend + REST/GraphQL API backend + relational database.
- Single-tenant internal deployment (not multi-tenant SaaS) — this is for Zevon AI's own staff, not a resellable product, unless stated otherwise.
- Hosted on the same cloud provider as zevonai.com's existing infrastructure, if applicable (TBD — confirm).
- Code-exercise grading likely needs a sandboxed code execution service (e.g. isolated containers) if auto-graded coding questions are required in v1.

## 8. Integrations (candidates for v1 or later)

| System | Purpose | Priority |
|---|---|---|
| Company SSO (Google/Microsoft) | Login | High |
| HRIS / employee directory | Auto-provision new hires, department/role data | Medium |
| Email provider (e.g. SendGrid/SES) | Notifications | High |
| Zevon AI's existing course/LMS platform | Reuse question bank or content, share candidate identity | Low (nice-to-have) |
| Slack | Notify managers of onboarding milestones | Low |

## 9. High-Level Data Model

- **User** (id, name, email, role, department, manager_id, status)
- **OnboardingTrack** (id, name, department/role, list of steps)
- **TrackAssignment** (user_id, track_id, status, due_date)
- **Assessment** (id, title, description, time_limit, pass_threshold, attempts_allowed, status: draft/published/archived, version)
- **Question** (id, type, prompt, options/answer_key, points, tags)
- **AssessmentQuestion** (assessment_id, question_id, order)
- **Attempt** (id, user_id, assessment_id, started_at, submitted_at, status, score)
- **AttemptAnswer** (attempt_id, question_id, response, auto_score, manual_score, reviewer_comment)
- **AuditLog** (actor_id, action, target, timestamp)

## 10. Success Metrics

- 100% of new hires complete required onboarding assessments before end of probation period.
- Reduce time-to-fully-onboarded (from offer-accept to sign-off) by a measurable amount vs. current manual process.
- Reviewer grading turnaround for manually-graded submissions under 48 hours.
- Admin can stand up a new onboarding track/assessment without engineering help (self-service authoring).

## 11. Assumptions & Open Questions

These need confirmation from stakeholders before this doc is finalized:

1. **Who exactly is being assessed?** — Assumed: internal new hires (any department), not external course students. Please confirm scope (e.g. is this only for instructors/mentors, or all staff including support/ops?).
2. **Assessment content types** — Assumed a mix of MCQ, code exercises, and manually-graded tasks, given Zevon AI's technical/cybersecurity focus. Confirm which types are actually needed for v1.
3. **SSO provider** — Assumed Google Workspace or Microsoft 365; confirm which the company uses internally.
4. **Relationship to the existing zevonai.com course platform** — Should this reuse any of that platform's infrastructure (question bank, AI assistant, code editor integration), or be fully independent?
5. **Volume** — Expected number of new hires per month/quarter, to size performance requirements.
6. **Code-exercise auto-grading** — Is sandboxed code execution actually required for v1, or can code questions be manually reviewed initially to reduce scope?
7. **Certificates** — Does completing onboarding assessments need to issue a verifiable certificate (mirroring the public platform's certificate feature)?
8. **Data retention & compliance** — Any specific regulatory requirements (e.g. GDPR, since students are from 10+ countries — does that extend to staff)?
9. **Timeline & budget constraints** for v1 launch.

## 12. Proposed Phasing

- **Phase 1 (MVP):** Admin creates assessments (MCQ + manual-grade types only) → assign to onboarding tracks → candidates take assessments → reviewers grade → basic dashboard/reporting.
- **Phase 2:** Auto-graded code exercises, SSO integration, email notifications, analytics.
- **Phase 3:** HRIS integration, Slack notifications, certificate issuance, advanced analytics.

## 13. Glossary

- **Track** — an ordered set of onboarding steps/assessments assigned to a new hire.
- **Attempt** — one instance of a candidate taking an assessment.
- **Reviewer** — a manager/lead responsible for grading and signing off a candidate's onboarding.
