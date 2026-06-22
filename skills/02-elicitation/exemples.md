
# Examples for Requirements Elicitation

## Example Invocation
```text
Read CASE.md, outputs/reviewed/01-inception.md, inputs/stakeholder-notes.md,
inputs/interview-answers.md, and inputs/assumptions.md.

Execute skills/02-elicitation/SKILL.md exactly as written.
Save the first AI output to outputs/raw/elicitation-ai-output.md.
Give every elicitation finding an EL ID.
Separate explicit needs from implicit needs.
Do not create final requirements yet.
```

## Example Input Summary
Case: Student Task Management System.

Stakeholders:
- Lecturer
- Student
- Administrator

Available evidence:
- Lecturers create assignments, set deadlines, grade submissions, and provide feedback.
- Students view assignments, submit files, monitor status, and track deadlines.
- Administrators manage users, courses, and configuration.
- Students want confirmation after upload.
- Administrators need accepted file type and maximum file size settings.

## Expected Output Example
```md
# Requirements Elicitation Output

## Elicitation Objectives
- Understand how lecturers create, monitor, grade, and provide feedback for assignments.
- Understand how students find assignments, submit files, and confirm submission status.
- Understand how administrators manage users, courses, enrollments, and assignment configuration.

## Elicitation Techniques
| Technique | Purpose | Stakeholder |
|---|---|---|
| Stakeholder Interview | Discover goals, pain points, and missing details. | Lecturer, Student, Administrator |
| Document Analysis | Extract known facts from CASE.md and stakeholder notes. | All stakeholders |
| Scenario Analysis | Understand assignment lifecycle from creation to grading. | Lecturer, Student |

## Interview Questions
### Lecturer
1. What information must be entered when creating an assignment?
2. How do you know which students have submitted or not submitted?
3. What information do you need before entering grades and feedback?

### Student
1. How do you know which assignments are due soon?
2. What confirmation do you need after submitting a file?
3. What status information do you need after submission?

### Administrator
1. What user and course data must be managed?
2. What assignment configuration settings are needed?
3. What reports are needed to monitor assignment activity?

## Elicitation Findings
| ID | Finding | Type | Stakeholder | Source | Rationale |
|---|---|---|---|---|---|
| EL-01 | Lecturers need to create assignments for specific courses. | Explicit | Lecturer | CASE.md | The case states that lecturers can create assignments. |
| EL-02 | Lecturers need to set assignment deadlines. | Explicit | Lecturer | CASE.md | The case states that lecturers can set deadlines. |
| EL-03 | Lecturers need to view submission status per assignment. | Explicit | Lecturer | stakeholder-notes.md | Lecturers need to see submitted and missing assignments. |
| EL-04 | Students need to submit assignment files. | Explicit | Student | CASE.md | The case states that students can submit files. |
| EL-05 | Students need confirmation after submitting files. | Explicit | Student | interview-answers.md | Students are worried that upload may fail. |
| EL-06 | Administrators need to configure accepted file types and maximum file size. | Explicit | Administrator | stakeholder-notes.md | Administrator notes mention these configuration settings. |
| EL-07 | The system may need a status model for submitted, late, graded, or returned assignments. | Implicit | Student | stakeholder-notes.md | Students need to monitor status, so status values must be clarified. |

## Explicit Needs
- Lecturer assignment creation and deadline setting.
- Student file submission and submission confirmation.
- Administrator user, course, and configuration management.

## Implicit Needs
- Assignment status categories must be defined.
- Upload validation rules must be available.

## Conflicts and Gaps
- Late submission handling is not fully defined.
- File type and file size limits are not specified.
- Report filters are not fully described.

## Assumptions
- ASSUMPTION: Users must authenticate before accessing assignment information.

## Open Questions
- OPEN QUESTION: What file types and maximum file size should be allowed?
- OPEN QUESTION: Should late submissions be rejected or stored with a Late status?
- OPEN QUESTION: What report filters are required?

## Quality Check Result
Passed. Each primary stakeholder has elicitation objectives, questions, and findings linked to sources.
```

## Bad Output Example
```md
EL-01: Students need mobile push notifications and chat with lecturers.
EL-02: The system must include plagiarism checking.
```

## Why This Output Is Bad
- The findings are not supported by the provided case.
- It invents features that are outside the current scope.
- It does not identify stakeholder source or rationale.
- It jumps from elicitation into solution features.

## Good Practice Notes
- Elicitation findings are evidence, not final requirements.
- Every finding should help the next skill create traceable requirements.
- If a need is useful but unsupported, mark it as an open question instead of treating it as fact.
