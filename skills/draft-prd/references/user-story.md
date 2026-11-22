# User Story Reference

Read this when writing the user stories in a PRD. Scenarios for each story are written per `gherkin-scenario.md`.

## Format

```
### User Story <n>: <short title>
**Covers:** <requirement IDs, e.g. R1.1, R1.2>

As a <user type>, I want to <do something> so that I can <accomplish something>.
```

## Rules

- **One goal per story.** If the story needs "and" to describe what the user wants, split it.
- **User type is a real role**, not "the user" or "the system". Use roles from the brief (e.g. "workspace admin", "first-time visitor"). If the brief names none, use the most specific role the problem statement implies and add an Open Question.
- **"I want to" is a user action or capability**, not a feature or UI element. Good: "save a set of filters". Bad: "have a Save button".
- **"So that I can" is the user's real motivation**, not a restatement of the action. Good: "reuse them next session without re-entering them". Bad: "so that I can save filters".
- **Cover requirements, don't restate them.** The story is the flow, the requirements are the rules. Every story lists the requirement IDs it covers, and every requirement is covered by at least one story.
- **Stay in scope.** A story must trace to an In Scope item. Never write a story for an Out of Scope item.
- **Order by user journey or priority**, with the core happy-path story first.
- **Size:** if a story would need more than about 6 scenarios, it's probably two stories.

## Check each story

Before keeping a story, confirm it is:

- **Independent**: can be understood without reading another story
- **Valuable**: the "so that" names a real user benefit
- **Testable**: you can write scenarios with an observable outcome
- **Small**: one goal, not a whole workflow

## Examples

Good:

```
### User Story 1: Save a filter set
**Covers:** R1.1, R1.2

As a workspace admin, I want to save my current filters under a name so that I can reapply them in later sessions without re-entering them.
```

Bad (and why):

- "As a user, I want a Save button so that I can save." Vague role, UI element instead of goal, circular benefit.
- "As an admin, I want to save, rename, share, and delete filters so that I can manage them." Four goals in one story. Split it.
- "As the system, I want to persist filters so that the database is updated." Not a user, and it's an implementation detail.
