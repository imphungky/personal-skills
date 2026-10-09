---
name: create-skill
description: Create or refine agent skills through collaborative definition of their purpose, core instructions, and case-specific references.
---

# Create Skill

A skill is a reusable set of instructions for a specific task or class of work.
It may define an ordered workflow, behavioral patterns, or both. Skills exist
to make an agent's actions consistent and purposeful, with clear outcomes and
case-specific guidance loaded only when needed.

Turn the user's intent into concise, explicit instructions that reliably
produce the intended behavior or result. Validation belongs to a separate skill.

## Process

1. Define the purpose. Establish when the skill should activate, the behavior
   it should guide, and its intended outcome. Use supplied context and examples;
   ask only about consequential gaps. Finish with a clear purpose and trigger.

2. Extract the core. Identify the essential workflow, behavioral patterns,
   or both. Keep instructions needed on every run in the core skill. Move
   case-specific guidance into references, with explicit conditions for when
   to consult them. Finish with the core instructions and reference boundaries.

3. Propose the structure. Present a concise outline of the core instructions,
   expected outcomes, and any references. Resolve consequential gaps with the
   user before drafting. If the user already supplied an agreed structure,
   proceed from it.

4. Draft and refine. Write `SKILL.md` within 100 lines, including frontmatter.
   Include a name and a description that clearly identifies when to use it.
   Choose headings suited to the task; make actions, behavioral patterns, and
   conditional branches explicit. State how the agent recognizes completion.
   Keep each instruction in one authoritative place and remove repetition or
   rules that do not contribute to the intended outcome. Use references for
   case-specific guidance, not to hide the core process. Incorporate user
   feedback and save the skill and any referenced files when requested.

The result is a concise skill whose core instructions are usable on their own,
with relative links and consultation conditions for any supporting references.
