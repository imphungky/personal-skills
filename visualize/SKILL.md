---
name: visualize
description: Create standalone HTML visualizations of solutions from agent sessions or context documents. Use when visual structure would help a user understand, refine, or maintain a mental model of a complex solution.
---

# Visualize a Solution

Create a clear HTML artifact that helps the user understand how a solution fits together and how it evolves over time. Prioritize enriching the user's mental model over visual decoration.

## Workflow

1. Read the provided session context, document, or solution description.
2. Identify:
   - Goals and constraints
   - Major components
   - Relationships and dependencies
   - User or system flows
   - Decisions and tradeoffs
   - Assumptions, risks, and open questions
3. Choose the visual structure that best represents the solution:
   - Architecture diagram
   - Process or user flow
   - State model
   - Decision map
   - Layered concept map
   - A combination of these
4. Create a standalone HTML file with embedded CSS and visuals. Do not require external tools, servers, or dependencies.
5. Include a concise summary explaining:
   - What the solution is
   - How its major parts fit together
   - What deserves the user's attention
6. Make uncertainty visible. Clearly distinguish confirmed decisions, assumptions, alternatives, risks, and unresolved questions.
7. Use visual hierarchy, labels, grouping, and whitespace to make relationships easy to follow.
8. Save the artifact at a predictable path, using `.visualize/<name>.html` by default.
9. When refining an existing visualization, preserve useful context while updating affected sections and reflecting what changed.
10. Review the HTML artifact in a browser for visual discrepancies, including overlapping elements, clipped text, broken layouts, poor contrast, inconsistent spacing, misleading connections, and unreadable labels. Fix any issues before delivering the artifact.

## HTML Guidelines

- Prefer semantic HTML, embedded CSS, and inline SVG where diagrams are useful.
- Keep the artifact readable when opened directly in a browser.
- Use accessible headings, labels, contrast, and text alternatives.
- Avoid visual complexity that does not improve understanding.
- Do not invent details. Mark missing information as unknown or unresolved.
- Keep the summary and visuals consistent with each other.

## Completion

The task is complete when the HTML artifact:

- Represents the major elements and relationships in the supplied context
- Gives the user a useful mental model of the solution
- Clearly identifies decisions, assumptions, and open questions
- Can be opened directly in a browser
- Includes a concise summary of the visualized solution
- Has been visually reviewed in a browser and corrected for layout or presentation issues
