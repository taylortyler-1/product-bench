---
name: draft-prd
description: Write a PRD from a product brief. Use when creating product requirements for a new feature or product. 
---

# Draft PRD

Write a product requirements document (PRD).

## Usage

```
/draft-prd $ARGUMENTS
```

## Roles

You are drafting the PRD. The user is the final approver. Your job is to produce a strong draft and surface what you're unsure about. The user decides what ships. Don't treat the PRD as final until they approve it.

## Asking questions

Ask the user when you're unsure. A question is cheaper than a wrong assumption baked into a PRD.

- Ask before drafting if the brief leaves out something the PRD depends on: who the user is, the evidence for the problem, what's in or out of scope, or how success is measured.
- Ask when the brief is ambiguous or conflicts with itself. Don't pick an interpretation silently.
- Ask when a decision is the user's to make, such as trade-offs between scope options or priorities.
- Group your questions and ask them together, with the most important first.
- Don't ask about things you can reasonably infer or that the references already cover. Don't ask just to ask.

### Recommending answers

- For judgment calls (scope, grouping requirements, which edge cases matter, a sensible metric), recommend an answer with a one-line reason, so the user can reply "yes" or "no, because...".
- Label recommendations as proposals, not facts, so they don't end up in the PRD as if the user had said them.
- Don't recommend answers to factual questions about users, evidence, or baselines. Ask them plainly. A guess there is fabrication.

### Unanswered questions

- If the user accepts a recommendation, use it in the PRD.
- If a question stays unanswered, don't guess. Put `TBD` in the section and list it under **Open Questions**, with your recommendation noted as a proposed default, not as PRD content.

## Rules

- Write only from the brief and any evidence the user gave you. Never invent metrics, quotes, user counts or research findings. If a section needs a fact you don't have, ask the user. If it stays unanswered, write `TBD` in the section and add it to **Open Questions**.
- Be specific and testable. Cut filler like "seamless", "intuitive", "robust", or "user-friendly".
- Describe **what** and **why**, not **how**. Don't prescribe UI layout, architecture, or technology unless the brief requires it.
- Keep every section short. A reader should get the point of each section in under a minute.
- Keep the headings and their order exactly as in the template. Downstream skills depend on them.
- Delete the template's instructional text from the output. The output should contain only real content.

## Workflow

1. **Read the brief.** Understand the feature, the user, and the problem.
2. **Ask questions.** Resolve gaps and ambiguities with the user before drafting (see Asking questions).
3. **Read the references.** Read `references/prd.md` for the template and section rules. Read `references/user-story.md` and `references/gherkin-scenario.md` before writing the stories.
4. **Draft the PRD** following the template.
5. **Run the final check** below and fix any failures.
6. **Present the draft to the user for approval.** Point out the open questions and any assumptions you made. Revise until they approve, then save the PRD.

## Final check

Before returning the PRD, verify:

- [ ] The Problem has who, how often, how painful, and evidence (or an explicit gap)
- [ ] No invented numbers, quotes, or research
- [ ] Nothing is both In Scope and Out of Scope
- [ ] Every requirement is testable, numbered, and covered by at least one story
- [ ] Every story has a happy path and at least one edge or error scenario
- [ ] No implementation details in Requirements or Scenarios
- [ ] All template instruction text and placeholders are removed
- [ ] Every gap is listed in Open Questions
