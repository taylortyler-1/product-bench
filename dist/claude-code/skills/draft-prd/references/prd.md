# PRD Reference

Read this when drafting a PRD. It has two parts: the **template** (the exact structure to output) and the **section rules** (what each section must contain and what to avoid).

Companion references:
- `user-story.md`: how to write a user story
- `gherkin-scenario.md`: how to write Gherkin scenarios

## Template

Output the PRD in this structure. Text in `<angle brackets>` is a placeholder to replace.

````markdown
# <Feature Name>

## Problem

<2-3 sentences: who has the problem, what it is, and the cost of leaving it unsolved.>

- **Who:** <user type or segment>
- **Frequency:** <how often it happens>
- **Severity:** <how painful it is>
- **Evidence:** <data, research, support tickets, quotes, or "None provided">

## Success Hypothesis

We believe that <the feature> will cause <user type> to <change in behavior>.
We'll know we're right when <one observable signal>.

- **Baseline:** <current value or TBD>
- **Target:** <target value or TBD>

## Scope

### In Scope
- <capability>

### Out of Scope
- <related capability, deferred> (<reason or "future">)

## Requirements

### <Functional Group>
- **R1.1** <The system must ...>
- **R1.2** <The system must ...>

### <Functional Group>
- **R2.1** <The system must ...>

## User Stories & Gherkin Scenarios

### User Story 1: <short title>
**Covers:** R1.1, R1.2

As a <user type>, I want to <do something> so that I can <accomplish something>.

```gherkin
Feature: <feature name>

  Scenario: <happy path>
    Given <starting state>
    When <user action>
    Then <observable outcome>

  Scenario: <edge case or error path>
    Given <starting state>
    When <user action>
    Then <observable outcome>
```

## Open Questions
- <question> (Owner: <name or TBD>)
````

## Section rules

### Feature Name
- Short noun phrase naming the capability, e.g. "Saved Search Filters". Not a sentence, not a ticket ID.

### Problem
- Describe the problem the user has, not the solution. If the sentence contains "add" or "build", you've written a solution.
- Cover **who** is affected, **how often**, and **how painful**.
- Ground it in evidence. If the user gave none, write `Evidence: None provided` and add an Open Question. Don't fabricate.
- Good: "Admins managing 50+ seats re-enter the same filters every session, about 10 times a day, and report it as their top annoyance in support tickets."
- Bad: "Users need a better filtering experience."

### Success Hypothesis
- Exactly one hypothesis: a belief about how the feature will change user behavior. Don't list several, and don't add secondary or guardrail metrics.
- It must trace back to the Problem. If the problem is "admins re-enter filters every session", the hypothesis is about that behavior, not overall engagement.
- The behavior change must be something users do, not something they feel. Good: "stop re-entering filters each session". Bad: "find filtering easier".
- The "We'll know we're right when" clause must name one observable signal, such as task completion, time on task, repeat use, or adoption. Without a signal the hypothesis can't be proven wrong. Prefer a behavior signal over a vanity count (page views, sign-ups).
- Writing the hypothesis is a judgment call. If the brief doesn't give one, propose it and confirm it with the user.
- Baseline and target are facts and numbers. Ask the user for them. Use `TBD` where unknown and add an Open Question. Never guess numbers.
- Good: "We believe that saved filters will cause workspace admins to stop re-entering filters each session. We'll know we're right when the share of sessions where an admin applies a saved filter reaches the target."
- Bad: "We believe that saved filters will improve the user experience."

### Scope
- **In Scope** lists capabilities, not tasks or implementation steps.
- **Out of Scope** lists things a reader might reasonably assume are included. Each item gets a short reason or "future". If nothing is plausibly adjacent, say "None identified". Don't pad.
- Everything in Requirements must trace to an In Scope item. Nothing in Out of Scope may appear in Requirements.

### Requirements
- Group by functional area (e.g. "Creating filters", "Managing saved filters"). 2-6 groups is typical.
- One testable statement per requirement. Use "must" for required behavior. Avoid "should", "may", "etc.", "and/or".
- Number requirements `R<group>.<item>` so stories can reference them. Don't renumber once published.
- State behavior, limits, and rules (e.g. "must support up to 20 saved filters per user"). Include error and empty states.
- Don't duplicate the user stories. Requirements are the rules, stories are the flows.

### User Stories & Gherkin Scenarios
- Write each story following `user-story.md` and its scenarios following `gherkin-scenario.md`. Read both before drafting this section.
- Every requirement must be covered by at least one story, and every story lists the requirements it covers in `Covers:`.
- Each story gets its own `gherkin` fenced block with at least one happy path and one edge or error scenario.

### Open Questions
- List every gap you hit while drafting: missing evidence, unknown metrics, ambiguous scope, conflicting information.
- Each question must be answerable and have an owner or `TBD`. If there are none, write "None".
