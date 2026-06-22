
# Requirements Elicitation

## Purpose
This skill guides AI to perform the elicitation stage of requirements engineering for the Student Task Management System. It helps identify elicitation techniques, prepare stakeholder interview questions, extract explicit needs, infer supported implicit needs, and document elicitation findings that can be used as input for requirements specification.

The problem solved by this skill is preventing AI from creating requirements without clear stakeholder evidence.

## When to Use
Use this skill after the inception output has identified the business problem, stakeholders, scope, assumptions, constraints, and open questions.

Use it when:
- Stakeholder needs must be discovered in more detail.
- Interview questions need to be prepared.
- Raw stakeholder notes and interview answers need to be converted into elicitation findings.
- Explicit and implicit needs must be separated.
- Findings must be given source IDs for traceability.

## Inputs
The following information must be available before this skill is executed:

- `CASE.md`
- `outputs/reviewed/01-inception.md`
- `inputs/stakeholder-notes.md`
- `inputs/interview-answers.md`
- `inputs/assumptions.md`

## Required Context
AI must read the following files before producing output:

- `CASE.md`
- `outputs/reviewed/01-inception.md`
- `inputs/stakeholder-notes.md`
- `inputs/interview-answers.md`
- `inputs/assumptions.md`

AI must use the inception output as the main project boundary. AI must not expand the scope unless the expansion is labeled as an assumption or open question.

## Workflow
1. Read all required context files.
2. Identify the elicitation objective for each primary stakeholder.
3. Select suitable elicitation techniques, such as stakeholder interview, document analysis, scenario analysis, and observation.
4. Prepare interview questions for lecturers, students, and administrators.
5. Extract explicit needs directly stated in the stakeholder notes and interview answers.
6. Identify implicit needs only when they are logically supported by the provided evidence.
7. Assign an elicitation ID to each finding using the format `EL-01`, `EL-02`, and so on.
8. For each finding, record stakeholder, need type, source, and rationale.
9. Identify conflicts, gaps, assumptions, and open questions.
10. Do not convert every finding directly into a requirement.
11. Run the quality checks.
12. Stop and request clarification if findings cannot be linked to a source.

## Output Format
The output must use the following structure:

```md
# Requirements Elicitation Output

## Elicitation Objectives

## Elicitation Techniques
| Technique | Purpose | Stakeholder |
|---|---|---|

## Interview Questions
### Lecturer
### Student
### Administrator

## Elicitation Findings
| ID | Finding | Type | Stakeholder | Source | Rationale |
|---|---|---|---|---|---|

## Explicit Needs

## Implicit Needs

## Conflicts and Gaps

## Assumptions

## Open Questions

## Quality Check Result
```

## Rules
- Every elicitation finding must have an ID.
- Every finding must include stakeholder and source.
- Use `Explicit` for needs directly stated in the source.
- Use `Implicit` only for needs strongly supported by the source.
- Do not invent stakeholder goals.
- Do not add unsupported features such as chat, plagiarism detection, mobile apps, or notifications unless the source provides them.
- Do not write final functional requirements in this skill.
- Mark assumptions with `ASSUMPTION`.
- Mark missing information with `OPEN QUESTION`.
- Keep questions open-ended and relevant to the stakeholder role.

## Quality Checks
Before finalizing the output, check that:

- Each primary stakeholder has elicitation objectives.
- At least one elicitation technique is selected for each primary stakeholder.
- Interview questions are specific to lecturer, student, and administrator needs.
- Each finding has an ID, stakeholder, source, and rationale.
- Explicit and implicit needs are separated.
- Unsupported assumptions are marked or removed.
- Conflicts and gaps are visible.
- The output can be used as input for the specification skill.

## Failure Conditions
The skill must stop or request clarification if:

- `outputs/reviewed/01-inception.md` is missing or empty.
- Stakeholder notes and interview answers are missing.
- Findings cannot be linked to a source.
- The provided context contradicts the inception scope.
- The AI must invent major stakeholder needs to complete the output.
- A conflict affects core scope and cannot be resolved or documented as an open question.

## Example Invocation
Read `CASE.md`, `outputs/reviewed/01-inception.md`, `inputs/stakeholder-notes.md`, `inputs/interview-answers.md`, and `inputs/assumptions.md`.

Execute `skills/02-elicitation/SKILL.md` exactly as written.

Save the raw result to `outputs/raw/elicitation-ai-output.md`.

Do not invent missing facts. Assign elicitation IDs and link every finding to a source.

## Expected Output Example
```md
## Elicitation Findings
| ID | Finding | Type | Stakeholder | Source | Rationale |
|---|---|---|---|---|---|
| EL-01 | Lecturers need to create assignments for specific courses. | Explicit | Lecturer | stakeholder-notes.md | The lecturer notes state that lecturers need to create assignments for courses. |
| EL-02 | Students need confirmation after submitting assignment files. | Explicit | Student | interview-answers.md | Students are worried that files may not be uploaded correctly. |
| EL-03 | Administrators need configurable file rules. | Implicit | Administrator | stakeholder-notes.md | File type and size settings imply that upload rules must be configurable. |

## Open Questions
- OPEN QUESTION: What file types and maximum file size should be accepted?
- OPEN QUESTION: Should late submissions be blocked or accepted with a Late status?
```
