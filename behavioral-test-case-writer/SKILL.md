---
name: behavioral-test-case-writer
description: Derive meaningful behavioral test cases from domain entities, inputs, and observable outcomes instead of starting with implementation contracts.
---

# Behavioral Test Case Writer

## Purpose

Use this skill when designing tests for a feature, vertical slice, or domain model. The goal is to describe how entities respond to meaningful inputs and produce observable outcomes. The result should be a set of behavioral scenarios that can guide implementation and reveal missing product decisions.

## Core approach

1. Identify the entities involved and what each one is responsible for.
2. Identify meaningful inputs: user actions, domain events, external messages, persisted state, and lifecycle events.
3. Describe the observable behavior that should follow each input.
4. Write scenarios in Given/When/Then form:
   - **Given** establishes relevant state and context.
   - **When** names one meaningful input or event.
   - **Then** states observable outcomes, including effects on collaborating entities when relevant.
5. Prefer scenarios that explain product behavior over tests that merely validate object shape, method calls, or implementation details.
6. Include normal, boundary, and failure scenarios only when they represent a behavior the product intentionally promises.
7. Identify unresolved behavioral decisions explicitly instead of silently inventing policies.

## Test-boundary guidance

- Use unit tests for entity/application behavior with collaborators replaced by small fakes.
- Use integration tests where behavior depends on real persistence, rendering, or transport integration.
- Use end-to-end tests for browser, process-launching, or cross-application workflows.
- Do not unit-test third-party internals. Test the behavior of the application around them.
- Treat serialization, validation, and protocol cases as supporting tests, not the primary source of scenarios, unless robustness itself is a stated requirement.

## Preferred scenario shape

```text
Given [meaningful starting state]
When [user action or domain event]
Then [observable result]
And [relevant side effect or collaborating-entity result]
```

Examples:

```text
Given no board has previously been saved
When the board application starts
Then it displays an empty canvas
```

```text
Given an open board with no connection
When the user draws a shape
Then the shape appears on the canvas
And the board is saved locally
```

```text
Given the board is open
When a connected client sends a scene update
Then the canvas displays the updated scene
```

## Output requirements

For each scenario, state:

- the entity or behavior under test;
- the meaningful input;
- the observable outcome;
- the appropriate test level;
- any product decision that must be clarified.

Finish by separating proposed unit, integration, and end-to-end scenarios. Do not begin by generating exhaustive malformed-input or mock-interaction tests. Add those only after the intended behavioral surface is clear.

## Completion criteria

The test set is complete enough when a reader can understand the feature’s intended behavior, its important state transitions, and the remaining behavioral decisions without seeing the implementation.
