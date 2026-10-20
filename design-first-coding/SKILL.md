---
name: design-first-coding
description: Guide substantial coding changes through explicit problem decomposition, module design, dependency review, and user approval before implementation. Use when a change meaningfully alters one module or the responsibilities or interactions of multiple modules; skip for small, mechanical, or localized fixes.
---

# Design-First Coding

## Purpose

Produce maintainable implementations by understanding the problem before changing code. Treat modules as information-hiding boundaries: expose a small, intuitive interface while keeping implementation complexity and volatile knowledge behind it.

## When to use

Activate when the requested change changes the meaning, responsibilities, or behavior of a substantial module, or changes the relationships between modules. Do not activate for typos, formatting, obvious one-line fixes, routine renames, or other mechanical edits with no meaningful design choice.

When uncertain, inspect enough of the request and codebase to decide whether the change is substantive; do not force this workflow onto trivial work.

## Workflow

1. **Understand the problem.** Restate the goal, users or callers affected, constraints, invariants, and observable outcomes. Inspect the relevant code, tests, configuration, and neighboring modules before proposing structure.
2. **Map the current system.** Identify the modules involved, each module's responsibility, public interfaces, ownership of important knowledge, existing dependencies, and behavior that must remain unchanged. Distinguish facts from assumptions and call out unresolved decisions.
3. **Decompose the change.** Explain what will be added, removed, changed, or deliberately left alone in each affected file or module. Trace the main data and control flows, including error and lifecycle paths where relevant.
4. **Propose the design.** Present the smallest coherent design: responsibilities, interfaces, data ownership, dependency direction, and why each boundary exists. Prefer simple interfaces that hide complexity rather than spreading it across callers. Keep each new or substantially modified file at 500 lines or fewer unless the user explicitly states otherwise. If an existing file already exceeds that limit, assess whether the change should split it, but do not introduce an unrelated refactor silently.
5. **Review module stakeholders.** For every proposed dependency or interface change, consider the modules that consume, implement, configure, test, or operate it. Check coupling, information leakage, circularity, duplicated knowledge, compatibility, and whether a dependency can be avoided or narrowed.
6. **Pause for approval.** Show the design, affected files, trade-offs, risks, and open questions. Do not implement substantive changes until the user approves. If the user critiques the design, revise the design and repeat this checkpoint.
7. **Implement deliberately.** After approval, make the smallest coherent set of changes. Keep public interfaces stable unless the approved design requires otherwise; update tests, documentation, and configuration needed to preserve the boundary.
8. **Verify the result.** Run relevant tests and checks. Re-read the changed modules as a system, inspect the cumulative diff, and confirm that dependencies, responsibilities, and observable behavior match the approved design. Report any deviation or unresolved risk.

## Design review questions

- What knowledge is each module hiding, and is its interface intuitive for its callers?
- Does each dependency represent a necessary relationship, or is it leaking implementation detail?
- Which module owns each piece of state, policy, transformation, and error handling?
- Could the design be simpler by removing an abstraction, dependency, or new concept?
- Will a likely future change be localized, or will it require coordinated edits across the dependency web?
- Are compatibility, failure behavior, testing boundaries, and operational concerns explicit?
- Do new or substantially modified files stay within the 500-line limit, or is an exception explicit?

## Completion criteria

For substantive work, completion requires user-approved design, implementation consistent with that design, relevant validation, and a final review showing no accidental dependency, responsibility, or behavior changes. For trivial work, complete the change directly with appropriate focused validation.
