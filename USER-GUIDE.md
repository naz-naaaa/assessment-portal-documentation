# Zevon AI Assessment Portal - User Guide

Welcome to the Zevon AI Assessment Portal, an internal onboarding and assessment system designed to help new staff complete their onboarding requirements and verify role-relevant skills.

---

## Table of Contents

1. [Overview](#overview)
2. [Getting Started](#getting-started)
3. [User Roles](#user-roles)
4. [Navigation](#navigation)
5. [For Candidates (New Hires)](#for-candidates-new-hires)
6. [For Reviewers (Managers/Team Leads)](#for-reviewers-managersteam-leads)
7. [For Admins (HR/L&D)](#for-admins-hrld)
8. [For Super Admins](#for-super-admins)
9. [Common Scenarios](#common-scenarios)
10. [Troubleshooting](#troubleshooting)
11. [FAQ](#faq)

---

## Overview

### What is the Assessment Portal?

The Zevon AI Assessment Portal is an internal tool for managing staff onboarding. It allows:

- **New hires** to complete assigned assessments and track their onboarding progress
- **Managers** to review and grade submissions and sign off on onboarding completion
- **HR/L&D teams** to create assessments, manage onboarding tracks, and monitor organization-wide progress

### Key Features

| Feature | Description |
|---------|-------------|
| **Assessments** | Multiple question types including multiple-choice, single-choice, short answer, file upload, and free-text |
| **Onboarding Tracks** | Organized sequences of assessments and tasks for different roles/departments |
| **Automated Grading** | Instant scoring for objective questions (multiple-choice, single-choice, short answer) |
| **Manual Review** | Human grading for subjective questions (free-text, file uploads) |
| **Progress Tracking** | Visual progress bars and status indicators for candidates and reviewers |
| **Reporting** | Onboarding funnel analytics and per-candidate reports with CSV/PDF export |

---

## Getting Started

### Creating Your Account (New Hires)

Before you can use the portal, an administrator must invite you. Once invited:

1. Open the registration link provided by HR
2. Enter your **work email address** (the same email that was invited)
3. Enter your **full name**
4. Create a **password** (must meet security requirements)
5. Click **Create account**

**Important:** The registration link is shared by all candidates. You must register using the exact email address that was invited - other email addresses will not work.

### Signing In

1. Go to the portal homepage
2. Click **Sign In** or **Employee Sign In**
3. Enter your email address and password
4. Click **Sign in**

#### Identity Verification (Candidates Only)

As a candidate, you will be asked to take a live photo using your webcam each time you sign in. This is a security measure to verify your identity.

1. After entering your credentials, a camera prompt will appear
2. Position your face in the camera view
3. Click **Take photo**
4. Click **Continue** to complete sign-in

**Note:** You must allow camera access in your browser for this feature to work. File uploads are not accepted - only live camera captures.

### Forgot Your Password?

1. On the sign-in page, click **Forgot password?**
2. Enter your email address
3. Click **Send reset link**
4. Check your email for a password reset link
5. Click the link and enter your new password
6. Return to the sign-in page and log in with your new password

---

## User Roles

The portal has four user roles with different levels of access:

| Role | Description | Can Access |
|------|-------------|------------|
| **Candidate** | New hire completing onboarding | Personal dashboard, assigned assessments, own results |
| **Reviewer** | Manager or team lead | Grading queue, direct reports' progress and checklists |
| **Admin** | HR or L&D staff | Everything Reviewers can access, plus: assessment creation, question bank, tracks, invites, reports |
| **Super Admin** | IT/Operations | Everything Admins can access, plus: integration settings (API keys) |

---

## Navigation

### Candidate Navigation

As a candidate, your main screen is the **Dashboard**, which shows:
- Your assigned onboarding track
- Progress bar showing overall completion
- List of assessments and tasks to complete
- Status of each step (Not started, In progress, Passed, etc.)

### Reviewer Navigation

Reviewers see a navigation bar with:
- **Candidates** - View and manage your direct reports' onboarding progress
- **Review Queue** - Grade submissions awaiting manual review

### Admin Navigation

Admins have access to a full navigation bar:
- **Tracks** - Create and manage onboarding tracks
- **Assessments** - Build and configure assessments
- **Question Bank** - Manage reusable questions
- **Invites** - Provision new hire accounts
- **Candidates** - View all candidates' progress
- **Reports** - Organization-wide onboarding analytics
- **Settings** - (Super Admin only) Integration settings

---

## For Candidates (New Hires)

### Your Dashboard

After signing in, you'll see your personal dashboard with:

#### Progress Overview
- Your assigned **onboarding track** name
- A **progress bar** showing how many steps you've completed
- Percentage of track completed

#### Active and Completed Tabs
- **Active** tab shows steps you still need to complete
- **Completed** tab shows steps you've finished

#### Step Cards
Each step shows:
- **Title** of the assessment or task
- **Type** (Assessment or Task)
- **Step number** in the sequence
- **Status** (Not started, In progress, Submitted, Needs review, Passed, Failed, Completed)
- **Due date** if one is set
- **Due date warning** if approaching or overdue

### Starting an Assessment

1. On your dashboard, click on an assessment card
2. In the right panel, review the **Assessment Summary** showing the timeline progress
3. Click **Start Assessment** (or **Resume assessment** if you started earlier)
4. Review the assessment details:
   - Time limit (if any)
   - Number of questions
   - Pass threshold percentage
   - Number of attempts allowed
5. Read the "Before you begin" tips
6. Click **Start assessment** to begin

#### Assessment Rules
- If timed, the timer starts immediately and cannot be paused
- You have a limited number of attempts (shown on the start screen)
- You may need to complete earlier tasks before starting certain assessments

### Taking an Assessment

Once you start an assessment:

#### Navigation
- **Question numbers** at the top let you jump to any question
- **Previous/Next buttons** navigate between questions
- A **progress bar** shows how far through the assessment you are
- The **save status** indicator shows "Saving...", "Saved", or "Couldn't save"

#### Answering Questions

Different question types require different answers:

| Question Type | How to Answer |
|---------------|---------------|
| **Single Choice** | Click one option from the list |
| **Multiple Choice** | Check all options that apply |
| **Short Answer** | Type your answer in the text field |
| **Free Text** | Write a detailed response in the text area |
| **File Upload** | Click the file input and select a file from your computer |

#### Auto-Save
Your answers are automatically saved:
- Every 20 seconds
- When you navigate to a different question

If you see "Couldn't save - retrying", check your internet connection.

#### Copy/Paste
Some assessments may disable copy and paste to maintain integrity. If copy/paste doesn't work, this restriction is intentional.

### Finishing an Assessment

1. Answer all questions (you can skip and return later)
2. Click **Finish assessment**
3. Confirm by clicking **Finish** in the confirmation dialog

**Warning:** You cannot change your answers after finishing.

### Timed Assessments

If your assessment has a time limit:
- A **countdown timer** appears in the header
- When time expires, the assessment **automatically submits**
- You cannot pause the timer once started

### Viewing Your Results

After completing an assessment:

1. Return to your dashboard
2. Click on the completed assessment
3. Click **View results**

The results page shows:
- **Overall score** (if graded)
- **Pass/Fail status** and threshold
- **Each question** with your answer
- **Points earned** per question
- **Reviewer feedback** (if provided and released)

#### Pending Review
If your assessment includes free-text or file-upload questions:
- Auto-graded questions show their scores immediately
- Manually-graded questions show "Pending review"
- Your overall score appears once a reviewer finishes grading

### Understanding Step Statuses

| Status | Meaning |
|--------|---------|
| **Not started** | You haven't begun this assessment/task yet |
| **In progress** | You've started but not submitted |
| **Submitted** | Submitted and awaiting auto-grading completion |
| **Needs review** | Submitted and awaiting manual grading |
| **Passed** | Graded and you met the pass threshold |
| **Failed** | Graded and you did not meet the pass threshold |
| **Completed** | (Tasks only) A reviewer has signed off on this task |

### Due Dates

- Due dates appear on each step card
- **"Due soon"** appears when a deadline is approaching
- **"Overdue"** appears when a deadline has passed
- Meeting due dates is important for your onboarding completion

---

## For Reviewers (Managers/Team Leads)

### Candidates List

Access via **Candidates** in the navigation.

This page shows all candidates you supervise (or all candidates if you're an Admin). For each candidate, you see:
- **Name**
- **Assigned track**
- **Onboarding status** (Not started, In progress, Completed)
- **Due date warnings** (Due soon, Overdue)

Click a candidate's name to view their full checklist.

### Candidate Checklist

The candidate detail page shows:

#### Header
- Candidate's name
- Login photo (most recent)
- Onboarding status badge
- **Export buttons** (CSV and PDF)

#### Onboarding Checklist
A list of all steps in the candidate's track:
- **Step number and title**
- **Type** (Assessment or Task)
- **Status** for assessment steps (Not started, In progress, Submitted, Passed, Failed)
- **Due date** and warnings
- **Sign-off checkbox** for task steps

#### Assessment Attempts
A history of all the candidate's assessment attempts showing:
- Assessment title
- Status
- Date started
- Time spent
- Score (if graded)
- Reviewer comments

### Signing Off Task Steps

Some onboarding steps are tasks (like "Sign NDA" or "Complete orientation") that don't have assessments. To mark a task complete:

1. Go to the candidate's checklist page
2. Find the task step
3. Click the checkbox to mark it complete

The system records who completed the sign-off and when.

### Grading Queue (Review Queue)

Access via **Review Queue** in the navigation.

This page lists all assessment submissions awaiting your manual review. For each entry, you see:
- **Candidate name**
- **Assessment title**
- **Number of questions to grade**
- **Submission date**

Click an entry to grade it.

### Grading an Assessment

The grading page shows all free-text and file-upload questions that need manual scoring.

For each question:
1. Read the question prompt
2. Review the candidate's answer
   - For file uploads, click the filename to download
3. Enter a **score** (0 to the maximum points for that question)
4. Optionally add a **comment** for feedback
5. Click **Save grade**

#### Overall Feedback
At the bottom of the page, you can add overall feedback for the entire attempt. This is visible to the candidate alongside their score.

### Exporting Reports

From any candidate's checklist page:

**CSV Export:**
1. Click the **CSV** button
2. A file downloads with all attempt data

**PDF Export:**
1. Click the **PDF** button
2. A print-friendly page opens in a new tab
3. Use your browser's print function (Ctrl+P or Cmd+P)
4. Choose "Save as PDF" as the destination

---

## For Admins (HR/L&D)

Admins have access to everything Reviewers can do, plus tools for creating and managing assessments, tracks, and invites.

### Managing Onboarding Tracks

Access via **Tracks** in the navigation.

#### What is a Track?
A track is a template for an onboarding program, such as "Cybersecurity Instructor Onboarding" or "Support Staff Onboarding". It contains an ordered list of assessments and tasks that candidates assigned to it must complete.

#### Viewing Tracks
The tracks page shows all existing tracks with:
- Track name
- Department (if assigned)
- Number of steps
- Number of candidates assigned

#### Creating a Track
1. Scroll to "Create New Track"
2. Enter a **track name** (e.g., "Developer Onboarding")
3. Optionally enter a **department**
4. Click **Create track**

#### Adding Steps to a Track
1. Click a track to open its detail page
2. Use the **Assign an assessment** dropdown to add assessments
3. Each assessment becomes a step in the track

### Managing Assessments

Access via **Assessments** in the navigation.

#### Viewing Assessments
The assessments page lists all assessments with:
- Title
- Status (Draft, Published, Archived)
- Version number
- Question count

#### Creating an Assessment
1. Scroll to "New assessment"
2. Enter a **title**
3. Optionally enter a **description**
4. Click **Create**

#### Configuring Assessment Rules
On an assessment's detail page, you can configure:

| Setting | Description |
|---------|-------------|
| **Time limit** | Minutes allowed (blank = unlimited) |
| **Pass threshold** | Minimum percentage to pass |
| **Attempts allowed** | How many times a candidate can try |
| **Randomize question order** | Show questions in random order each attempt |
| **Question pool size** | Select a random subset of questions per attempt |
| **Disable copy/paste** | Prevent copying text in the assessment |
| **Release feedback** | Show reviewer comments to candidates |

#### Adding Questions to an Assessment
1. Open the assessment detail page
2. **Add from question bank:** Use the picker to select existing questions
3. **Write a new question:** Use the form at the bottom

#### Assessment Statuses

| Status | Meaning |
|--------|---------|
| **Draft** | Still being edited, not visible to candidates |
| **Published** | Active and available to assigned candidates |
| **Archived** | Preserved for historical records, no longer available |

Use the action buttons to Publish, Archive, or Duplicate an assessment.

#### Previewing an Assessment
1. Click **Preview as candidate** on the assessment detail page
2. See exactly how candidates will experience the assessment
3. Note: You cannot submit answers in preview mode

#### Viewing Assessment Analytics
1. Click **Analytics** on the assessment detail page
2. View metrics including:
   - Number of graded attempts
   - Average score
   - Pass rate
   - Question-level difficulty (% correct)
   - Time spent distribution

### Managing the Question Bank

Access via **Question Bank** in the navigation.

#### What is the Question Bank?
The question bank stores reusable questions that can be added to multiple assessments. Questions are organized with tags for easy filtering.

#### Filtering Questions
Use the filter dropdowns to find questions by:
- **Skill** (e.g., JavaScript, Python)
- **Role** (e.g., Developer, Support)
- **Topic** (e.g., Security, Networking)

#### Creating Questions

The wizard offers three methods:

**1. Create Manually**
1. Choose "Create manually"
2. Select question type
3. Enter the prompt
4. Configure options (for choice questions)
5. Set points value
6. Add tags
7. Click **Save**

**2. Generate from Topic**
1. Choose "Generate from topic"
2. Enter a topic or subject (e.g., "Network security fundamentals")
3. Optionally paste reference content
4. Choose difficulty and count
5. Click **Generate questions**
6. Review and edit each generated question
7. Save the ones you want

**3. Import from PDF**
1. Choose "Import from PDF"
2. Upload a PDF file containing questions
3. Click **Extract questions**
4. Review and edit extracted questions
5. Save the ones you want

**Note:** PDF import requires the Mistral AI integration to be configured (Super Admin setting).

#### Question Types

| Type | Description | Grading |
|------|-------------|---------|
| **Single Choice** | One correct answer from multiple options | Automatic |
| **Multiple Choice** | Multiple correct answers from options | Automatic |
| **Short Answer** | Brief text response | Automatic (exact match) |
| **Free Text** | Extended written response | Manual review |
| **File Upload** | Candidate uploads a file | Manual review |

### Managing Invites

Access via **Invites** in the navigation.

#### Understanding Invites
Before someone can create an account, you must invite their email address. The invitation makes that specific email eligible to register.

#### Registration Link
A shared registration link is shown at the top of the page. Share this link with all invited candidates - they'll each register with their own email.

#### Inviting Individuals
1. Enter the **email address**
2. Select a **role** (usually CANDIDATE)
3. Optionally select an **onboarding track**
4. Optionally set a **track due date**
5. Click **Send invite**

#### Bulk Import via CSV
1. Prepare a CSV file with columns:
   - `email` (required)
   - `role` (optional, defaults to CANDIDATE)
2. Upload the file
3. Optionally select a track and due date
4. Click **Import CSV**
5. Review results showing which emails were invited

### Reports Dashboard

Access via **Reports** in the navigation.

The reports page shows an organization-wide view of onboarding progress.

#### Onboarding Funnel
Four metrics cards showing active hires:
- **Not started** - Haven't begun any assessments
- **In progress** - Currently working through their track
- **Completed** - Finished all requirements
- **Overdue** - Past their due date

A progress bar visualizes the overall funnel.

#### Overdue Candidates
A list of candidates who are past their due dates. Click any name to view their full checklist.

---

## For Super Admins

Super Admins have access to everything Admins can do, plus integration settings.

### Integration Settings

Access via **Settings** in the navigation.

#### Mistral AI Integration
The portal can use Mistral AI to automatically extract questions from uploaded PDF documents.

**To configure:**
1. Go to Settings
2. In the Mistral AI section, enter your API key
3. Click **Save**

**Security notes:**
- The API key is encrypted at rest
- Only Super Admins can view or modify the key
- The displayed key is masked (e.g., `sk-****1234`)

---

## Common Scenarios

### Scenario: New Hire's First Day

1. **HR invites the new hire's email** via the Invites page, assigning them to an onboarding track
2. **HR shares the registration link** with the new hire
3. **New hire registers** using their invited email
4. **New hire signs in** and takes the required identity photo
5. **New hire views their dashboard** showing assigned assessments
6. **New hire completes assessments** one by one
7. **Reviewer grades** any free-text submissions
8. **Reviewer signs off** on task steps
9. **Dashboard shows completion** when all steps are passed/completed

### Scenario: Retaking a Failed Assessment

1. Candidate completes an assessment but doesn't pass
2. Dashboard shows "Failed" status with the score
3. If attempts remain, candidate can click **Start Assessment** again
4. Candidate retakes the assessment
5. New attempt replaces the previous result

**Note:** If no attempts remain, the candidate sees "You've used all attempts" and cannot retake.

### Scenario: Dealing with Overdue Items

1. Reviewer sees "Overdue" badge on a candidate in their list
2. Reviewer clicks to view the candidate's checklist
3. Reviewer identifies which steps are incomplete
4. Reviewer follows up with the candidate directly
5. Reviewer may manually sign off on task steps if appropriate

### Scenario: Creating a New Assessment from Scratch

1. Admin goes to **Assessments** and creates a new assessment
2. Admin sets rules (time limit, pass threshold, attempts)
3. Admin adds questions from the bank or creates new ones
4. Admin clicks **Preview** to review the candidate experience
5. Admin clicks **Publish** to make it available
6. Admin goes to **Tracks** and adds the assessment to relevant tracks
7. Candidates assigned to those tracks see the new assessment

---

## Troubleshooting

### Cannot Register

| Problem | Solution |
|---------|----------|
| "Email not invited" | Ask HR to invite your email address first |
| Link doesn't work | Ensure you're using the correct registration URL |
| Password rejected | Ensure your password meets the requirements shown |

### Cannot Sign In

| Problem | Solution |
|---------|----------|
| Wrong password | Use the "Forgot password?" link to reset |
| Camera won't work | Allow camera permissions in your browser settings |
| Camera error message | Try a different browser (Chrome recommended) |

### Assessment Issues

| Problem | Solution |
|---------|----------|
| Answers not saving | Check your internet connection; the system auto-retries |
| Timer ran out | The assessment auto-submitted; check results in dashboard |
| Can't start assessment | You may need to complete a prerequisite task first |
| No attempts left | Contact your reviewer or HR about additional attempts |

### Grading Issues

| Problem | Solution |
|---------|----------|
| Can't see candidate | Reviewers only see their direct reports; Admins see all |
| Score won't save | Ensure score is within 0 and the question's max points |

---

## FAQ

### General

**Q: Who can see my assessment results?**
A: Only you, your assigned reviewer(s), and Admins/Super Admins can see your results.

**Q: Why do I need to take a photo when signing in?**
A: The identity photo helps verify that you are the person completing your assessments.

**Q: Can I use the portal on my phone?**
A: The portal is designed for desktop/tablet use. A keyboard is recommended for coding questions.

### Assessments

**Q: Can I pause a timed assessment?**
A: No, once started, the timer runs continuously until submission or time expiry.

**Q: What if I lose internet connection during an assessment?**
A: Your answers are saved every 20 seconds and when you change questions. Reconnect and continue - your progress should be preserved.

**Q: Can I change my answers after submitting?**
A: No, submissions are final. If you have attempts remaining, you can start a new attempt.

**Q: When will I see my score for free-text questions?**
A: After a reviewer grades them, which should happen within 48 hours.

### For Reviewers

**Q: How do I know when something needs grading?**
A: Check the Review Queue regularly. Submissions appear there automatically.

**Q: Can I change a grade after saving it?**
A: Yes, return to the grading page and update the score.

### For Admins

**Q: How do I remove someone from a track?**
A: **Needs verification** - This may require database-level changes or is handled through a different process.

**Q: Can I delete an assessment with submissions?**
A: No, archive it instead to preserve historical records.

**Q: How do I change a candidate's role?**
A: **Needs verification** - This may require Super Admin access or database changes.

---

## Need More Help?

If you encounter issues not covered in this guide:
1. Contact your HR representative or IT support
2. For technical issues, raise a support ticket with your IT team

---

*Last updated: August 2026*
*Zevon AI Assessment Portal - Internal Use Only*
