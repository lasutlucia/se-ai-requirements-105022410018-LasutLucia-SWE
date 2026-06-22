
# Examples for Project Inception and Stakeholder Discovery

## Example Invocation
```text
Read CASE.md, inputs/stakeholder-notes.md, and inputs/assumptions.md.
Execute skills/01-inception/SKILL.md exactly as written.
Save the first AI output to outputs/raw/inception-ai-output.md.
Do not invent missing facts.
Label assumptions with ASSUMPTION.
Label missing information with OPEN QUESTION.
```

## Example Input Summary
Case: Student Task Management System.

Known facts:
- Lecturers can create assignments, set deadlines, grade submissions, and provide feedback.
- Students can view assignments, submit files, monitor status, and track deadlines.
- Administrators can manage users, courses, and system configuration.
- The system must consider usability, security, performance, reliability, and data integrity.

## Expected Output Example
```md
# Project Inception Output

## Business Problem
Lecturers, students, and administrators need a consistent way to manage assignment information from assignment creation until grading and reporting. Without a centralized workflow, assignment status, deadlines, submissions, and feedback can become difficult to monitor and verify.

## Business Goals
- Centralize assignment creation, submission, grading, feedback, and reporting.
- Improve student visibility of deadlines and submission status.
- Help lecturers monitor submitted, missing, late, graded, and returned assignments.
- Help administrators maintain consistent user, course, and configuration data.

## Stakeholders
| Stakeholder | Type | Needs | Source |
|---|---|---|---|
| Lecturer | Primary | Create assignments, set deadlines, monitor submissions, grade work, and provide feedback. | CASE.md |
| Student | Primary | View assignments, submit files, monitor status, and track deadlines. | CASE.md |
| Administrator | Primary | Manage users, courses, and configuration. | CASE.md |

## Scope
### In Scope
- Assignment creation and deadline management.
- Student file submission.
- Submission status tracking.
- Grading and feedback.
- User, course, and configuration management.
- Basic assignment reporting.

### Out of Scope
- Plagiarism detection.
- Real-time chat.
- Video conferencing.
- Payment features.

## Assumptions
- ASSUMPTION: Users must authenticate before accessing assignment data.
- ASSUMPTION: Late submission policy can be configured by an administrator.

## Constraints
- Requirements must consider usability, security, performance, reliability, and data integrity.
- Requirements must be testable and traceable.

## Open Questions
- OPEN QUESTION: What file types and maximum file size should be accepted?
- OPEN QUESTION: Should late submissions be blocked or accepted with a Late status?
- OPEN QUESTION: What reports are required by lecturers and administrators?

## Quality Check Result
Passed. Stakeholders, scope, assumptions, constraints, and open questions are clearly separated.
```

## Bad Output Example
```md
The system should include chat, plagiarism detection, push notifications, and a mobile application because these features are useful for students.
```

## Why This Output Is Bad
- Chat, plagiarism detection, push notifications, and a mobile application are not supported by the provided case.
- The output jumps directly into features before clarifying the business problem.
- The output does not label assumptions.
- The output does not define stakeholders, scope, constraints, or open questions.

## Good Practice Notes
- Inception output should not become a full requirements specification.
- Every unsupported idea must be removed or labeled as an assumption or open question.
- The output from this skill should become the input for the elicitation skill.
