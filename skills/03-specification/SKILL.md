
# Requirements Elaboration and Specification

## Purpose
This skill guides AI to transform reviewed inception and elicitation outputs into structured requirements artifacts for the Student Task Management System. It produces functional requirements, non-functional requirements, business rules, user stories, and acceptance criteria that are clear, testable, measurable, and traceable.

The problem solved by this skill is preventing AI from producing vague, duplicated, unsupported, or untestable requirements.

## When to Use
Use this skill after the inception and elicitation outputs have been reviewed.

Use it when:
- Elicitation findings already have source IDs such as `EL-01`.
- Functional requirements must be written from stakeholder needs.
- Non-functional requirements must be made measurable.
- Business rules must be separated from system features.
- User stories and acceptance criteria must be created.
- The project needs output for `outputs/reviewed/03-requirements.md` and `outputs/reviewed/04-user-stories.md`.

## Inputs
The following information must be available before this skill is executed:

- `CASE.md`
- `outputs/reviewed/01-inception.md`
- `outputs/reviewed/02-elicitation.md`
- `inputs/assumptions.md`

## Required Context
AI must read the following files before producing output:

- `CASE.md`
- `outputs/reviewed/01-inception.md`
- `outputs/reviewed/02-elicitation.md`
- `inputs/assumptions.md`

AI must treat reviewed inception and elicitation outputs as the approved source. AI must not add features that are outside scope unless they are clearly marked as assumptions, open questions, or excluded items.

## Workflow
1. Read all required context files.
2. Extract candidate functional requirements from elicitation findings.
3. Assign each functional requirement an ID using `FR-01`, `FR-02`, and so on.
4. Link each functional requirement to one or more elicitation source IDs.
5. Identify non-functional requirements related to usability, security, performance, reliability, and data integrity.
6. Assign non-functional requirement IDs using `NFR-01`, `NFR-02`, and so on.
7. Rewrite vague non-functional statements into measurable criteria.
8. Identify business rules and assign IDs using `BR-01`, `BR-02`, and so on.
9. Create user stories using the format `As a [role], I want [capability], so that [benefit]`.
10. Assign user story IDs using `US-01`, `US-02`, and so on.
11. Create at least two acceptance criteria for each user story.
12. Assign acceptance criteria IDs using `AC-01`, `AC-02`, and so on.
13. Use Given-When-Then wording where possible.
14. Remove duplicate, unsupported, ambiguous, or untestable requirements.
15. Record assumptions and open questions that affect specification quality.
16. Run the quality checks.
17. Stop and request clarification if a requirement cannot be traced or tested.

## Output Format
The output must be split into two reviewed artifacts:

### `outputs/reviewed/03-requirements.md`
```md
# Requirements Specification

## Functional Requirements
| ID | Requirement | Stakeholder | Source |
|---|---|---|---|

## Non-Functional Requirements
| ID | Requirement | Measurement / Test |
|---|---|---|

## Business Rules
| ID | Rule | Source |
|---|---|---|

## Assumptions

## Open Questions

## Quality Check Result
```

### `outputs/reviewed/04-user-stories.md`
```md
# User Stories and Acceptance Criteria

## User Stories
### US-01: [Short Title]
As a [role], I want [capability], so that [benefit].

Related requirements: `FR-xx`

Acceptance criteria:
- AC-01: Given [context], when [action], then [expected result].
- AC-02: Given [context], when [failure or alternate condition], then [expected result].
```

## Rules
- Use requirement IDs consistently.
- Use `FR` only for functional requirements.
- Use `NFR` only for measurable quality requirements.
- Use `BR` only for business rules or domain policies.
- Use `US` only for user stories.
- Use `AC` only for acceptance criteria.
- Every functional requirement must be traceable to elicitation findings.
- Do not create requirements that are not supported by the case or elicitation output.
- Do not use ambiguous words such as fast, easy, secure, reliable, or user-friendly without measurable criteria.
- Do not combine multiple unrelated functions into one requirement.
- Do not write acceptance criteria that cannot pass or fail.
- Do not create user stories without related functional requirements.
- Keep assumptions and open questions separate from confirmed requirements.

## Quality Checks
Before finalizing the output, check that:

- There are at least 8 functional requirements.
- There are at least 4 measurable non-functional requirements.
- There are at least 2 business rules.
- There are at least 6 user stories.
- Each user story has at least 2 acceptance criteria.
- Every functional requirement has a stakeholder and source.
- Every user story links to one or more functional requirements.
- Every acceptance criterion is testable.
- No requirement is duplicated.
- No requirement is unsupported by the approved context.
- Non-functional requirements include measurable tests or thresholds.
- Business rules are separated from functional requirements.

## Failure Conditions
The skill must stop or request clarification if:

- `outputs/reviewed/02-elicitation.md` is missing or does not contain source IDs.
- A functional requirement cannot be traced to a stakeholder need or elicitation finding.
- A non-functional requirement cannot be measured or tested.
- A user story has no stakeholder value.
- Acceptance criteria cannot be objectively verified.
- Required context contains unresolved conflicts that affect core requirements.
- The AI must invent major product features to satisfy the minimum output count.

## Example Invocation
Read `CASE.md`, `outputs/reviewed/01-inception.md`, `outputs/reviewed/02-elicitation.md`, and `inputs/assumptions.md`.

Execute `skills/03-specification/SKILL.md` exactly as written.

Save raw AI output to `outputs/raw/requirements-ai-output.md`.

After human review, save final requirements to `outputs/reviewed/03-requirements.md` and final user stories to `outputs/reviewed/04-user-stories.md`.

Do not invent missing facts. Use requirement IDs, measurable non-functional requirements, and testable acceptance criteria.

## Expected Output Example
```md
## Functional Requirements
| ID | Requirement | Stakeholder | Source |
|---|---|---|---|
| FR-01 | The system shall allow lecturers to create assignments with title, description, course, deadline, and submission instructions. | Lecturer | EL-01, EL-02 |

## Non-Functional Requirements
| ID | Requirement | Measurement / Test |
|---|---|---|
| NFR-01 | The student assignment dashboard shall load within 3 seconds for 95% of requests under 100 concurrent users. | Performance test result |

## Business Rules
| ID | Rule | Source |
|---|---|---|
| BR-01 | A student can submit only to assignments linked to courses where the student is enrolled. | ASSUMPTION A-01 |

## User Story
### US-01: Create Assignment
As a lecturer, I want to create an assignment for a course, so that students know what task they must complete.

Related requirements: FR-01

Acceptance criteria:
- AC-01: Given an authenticated lecturer is assigned to a course, when the lecturer enters valid assignment data, then the assignment is saved and visible in the course.
- AC-02: Given required fields are missing, when the lecturer submits the form, then the system rejects the form and shows validation messages.
```
