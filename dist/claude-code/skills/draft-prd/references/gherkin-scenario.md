# Gherkin Scenario Reference

Read this when writing the scenarios for a user story in a PRD. Each story gets its own `gherkin` fenced block directly under the story text.

## Structure

````markdown
```gherkin
Feature: <feature name>

  Background:
    Given <state shared by every scenario below>

  Scenario: <happy path>
    Given <starting state>
    When <one user action>
    Then <observable outcome>

  Scenario: <edge or error case>
    Given <starting state>
    When <one user action>
    Then <observable outcome>
```
````

- Tag the fence `gherkin`.
- One `Feature:` per block. Name it after the story's goal.
- Indent `Background:` and `Scenario:` by 2 spaces, steps by 4.
- `Background:` is optional. Use it only when every scenario in the block starts with the same `Given` steps.

## Step rules

- **Given** is the starting state (data, permissions, what's already on screen). It is not an action.
- **When** is a single user action or event. Use one `When` per scenario. If you need two, you have two scenarios.
- **Then** is an outcome someone can observe: what the user sees, what is saved, what is blocked. Don't assert internal state ("the database row is created").
- Use `And` / `But` to add more steps of the same type. Never start a scenario with `And`.
- Write in present tense, third person ("the admin saves the filter"), or consistently in the story's user type.
- Describe behavior, not UI mechanics. Good: "When the admin saves the filter". Bad: "When the admin clicks the blue Save button in the top right".
- Use concrete values where they matter to the rule ("21st filter", "a name over 50 characters"), and leave them out where they don't.

## Scenario names

- Name the scenario for the situation and result, not the steps: "Saving a filter with a duplicate name is rejected".
- Names must be unique within the block.

## What to cover

Each story needs:

1. **At least one happy path.**
2. **At least one edge or error path.** Pick from: invalid input, empty state, limit reached, permission denied, duplicate, cancel or abandon, network or system failure.

Each scenario should map to a requirement from the story's `Covers:` line. If a requirement has no scenario, add one. If a scenario tests behavior no requirement states, either add the requirement or remove the scenario.

## Anti-patterns

- **Too many steps.** More than about 6 steps per scenario usually means it's testing a workflow. Split it.
- **Implementation detail.** Mentioning APIs, tables, or components. Keep it user-visible.
- **Vague outcomes.** "Then it works" or "Then the user is happy". State what is observable.
- **Chained actions.** `When` followed by `And` more actions. Use separate scenarios.
- **Scenarios that depend on each other.** Each must set up its own state through `Given`.
- **Untestable wording.** "quickly", "properly", "appropriate message". Use a number or exact text.
- **Tables and parameterized scenarios.** Don't use `Scenario Outline` or `Examples:` tables. Write each case as its own `Scenario`.

## Example

```gherkin
Feature: Save a filter set

  Background:
    Given the admin is on the members list with filters applied

  Scenario: Saving a filter set with a valid name
    When the admin saves the filters as "Active EMEA"
    Then "Active EMEA" appears in the admin's saved filters
    And the current filters remain applied

  Scenario: Saving a filter set with a duplicate name is rejected
    Given the admin already has a saved filter named "Active EMEA"
    When the admin saves the filters as "Active EMEA"
    Then the filters are not saved
    And the admin is told the name is already in use

  Scenario: Saving beyond the limit is blocked
    Given the admin already has 20 saved filters
    When the admin saves the filters as "Overflow"
    Then the filters are not saved
    And the admin is told the limit of 20 has been reached
```
