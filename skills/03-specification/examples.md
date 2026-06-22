
# Examples for Requirements Elaboration and Specification

## Example Invocation
```text
Read CASE.md, outputs/reviewed/01-inception.md,
outputs/reviewed/02-elicitation.md, and inputs/assumptions.md.

Execute skills/03-specification/SKILL.md exactly as written.
Save the first AI output to outputs/raw/requirements-ai-output.md.
After review, save final requirements to outputs/reviewed/03-requirements.md.
Save final user stories to outputs/reviewed/04-user-stories.md.
Use FR, NFR, BR, US, and AC IDs.
Do not create unsupported requirements.
```

## Example Input Summary
Approved elicitation findings:

- `EL-01`: Lecturers need to create assignments for specific courses.
- `EL-02`: Assignments need title, description, deadline, and submission instructions.
- `EL-03`: Lecturers need to view submitted and missing submissions.
- `EL-04`: Lecturers need to enter grades and feedback.
- `EL-05`: Students need to view active assignments and deadlines.
- `EL-06`: Students need to upload assignment files.
- `EL-07`: Students need confirmation after submission.
- `EL-08`: Students need to monitor submitted, late, graded, or returned status.
- `EL-09`: Administrators need to manage lecturer and student accounts.
- `EL-10`: Administrators need to manage courses and enrollments.
- `EL-11`: Administrators need accepted file type, maximum file size, and late submission settings.
- `EL-12`: Administrators need assignment activity reports.

## Expected Output Example: Requirements
```md
# Requirements Specification

## Functional Requirements
| ID | Requirement | Stakeholder | Source |
|---|---|---|---|
| FR-01 | The system shall allow lecturers to create assignments with title, description, course, deadline, and submission instructions. | Lecturer | EL-01, EL-02 |
| FR-02 | The system shall allow students to submit a file for an assignment before or after the deadline according to the configured late submission policy. | Student | EL-06, EL-11 |
| FR-03 | The system shall display active assignments and deadlines to students. | Student | EL-05 |
| FR-04 | The system shall show assignment status values to students: Not Submitted, Submitted, Late, Graded, and Returned. | Student | EL-07, EL-08 |
| FR-05 | The system shall allow lecturers to view a submission list per assignment, including student name, submission time, file link, status, grade, and feedback status. | Lecturer | EL-03 |
| FR-06 | The system shall allow lecturers to enter grades and written feedback for submitted assignments. | Lecturer | EL-04 |
| FR-07 | The system shall allow administrators to create, update, deactivate, and view lecturer and student accounts. | Administrator | EL-09 |
| FR-08 | The system shall allow administrators to create, update, and view courses and enrollment relationships. | Administrator | EL-10 |
| FR-09 | The system shall allow administrators to configure accepted file types, maximum file size, and late submission policy. | Administrator | EL-11 |
| FR-10 | The system shall provide reports showing assignment count, submitted count, missing count, and late submission count by course. | Administrator | EL-12 |

## Non-Functional Requirements
| ID | Requirement | Measurement / Test |
|---|---|---|
| NFR-01 | The system shall require authenticated access before a user can view or modify assignment data. | 100% of protected pages redirect unauthenticated users to login. |
| NFR-02 | The student assignment dashboard shall load within 3 seconds for 95% of requests under 100 concurrent users. | Performance test result. |
| NFR-03 | The system shall record create, update, submit, grade, and configuration actions in an audit log. | Audit log entry exists for each tested action. |
| NFR-04 | The system shall maintain assignment, submission, grade, and feedback data without orphan records. | Database integrity test shows zero orphan records after tested workflows. |

## Business Rules
| ID | Rule | Source |
|---|---|---|
| BR-01 | A student can submit only to assignments linked to courses where the student is enrolled. | ASSUMPTION A-01 |
| BR-02 | A lecturer can grade only assignments for courses assigned to that lecturer. | CASE.md |
| BR-03 | If submission time is later than the deadline and late submission is allowed, the submission status shall be Late. | EL-11 |

## Quality Check Result
Passed. Requirements are separated by type, measurable where needed, and traceable to sources.
```

## Expected Output Example: User Stories
```md
# User Stories and Acceptance Criteria

## US-01: Create Assignment
As a lecturer, I want to create an assignment for a course, so that students know what task they must complete.

Related requirements: FR-01

Acceptance criteria:
- AC-01: Given an authenticated lecturer is assigned to a course, when the lecturer enters title, description, course, deadline, and instructions, then the assignment is saved and visible in the course.
- AC-02: Given required assignment fields are missing, when the lecturer submits the form, then the system rejects the form and shows field-level validation messages.

## US-02: Submit Assignment
As a student, I want to submit an assignment file, so that my lecturer can assess my work.

Related requirements: FR-02

Acceptance criteria:
- AC-03: Given a student is enrolled in the course, when the student uploads an allowed file within the size limit, then the submission is saved with timestamp and status.
- AC-04: Given the uploaded file type or size is not allowed, when the student submits the file, then the system rejects the upload and explains the reason.

## US-03: Track Assignment Status
As a student, I want to view assignment status and deadlines, so that I can manage my tasks.

Related requirements: FR-03, FR-04

Acceptance criteria:
- AC-05: Given a student opens the dashboard, when active assignments exist, then the system displays each assignment deadline and status.
- AC-06: Given a submission has been graded, when the student views the assignment, then the system displays status Graded.
```

## Bad Output Example
```md
FR-01: The system must be fast and easy to use.
FR-02: The system should have chat, notifications, plagiarism detection, and mobile apps.
US-01: As a user, I want everything to work, so that I am happy.
AC-01: The system works correctly.
```

## Why This Output Is Bad
- `FR-01` is not a functional requirement and uses vague quality words.
- `FR-02` adds unsupported features not found in the approved context.
- `US-01` uses a vague role and unclear value.
- `AC-01` is not testable because it has no specific pass or fail condition.
- The output does not separate functional requirements, non-functional requirements, business rules, user stories, and acceptance criteria.

## Good Practice Notes
- A requirement should describe one clear capability or quality target.
- A non-functional requirement must be measurable.
- A business rule should describe a policy or domain constraint.
- Acceptance criteria should be written so a tester can verify pass or fail.
- If the AI cannot trace a requirement to a source, it should not become part of the baseline.
