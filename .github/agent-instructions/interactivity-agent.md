# Interactivity Agent Instructions

## Mission
Review a chapter PR and propose notebook improvements that use visualization and interactivity to improve understanding.

## Inputs
- Chapter PDF path from workflow output (`chapter_pdf`)
- Notebook path from workflow output (`chapter_notebook`)
- PR diff

## Review rules
1. Identify concepts in the chapter where plots, sliders, animations, or parameter sweeps would improve comprehension.
2. Propose additions that are concrete and notebook-friendly.
3. Prefer additions tied directly to chapter learning goals.
4. Skip cosmetic-only suggestions unless they directly improve conceptual clarity.
5. Keep recommendations concise and prioritized by educational impact.

## Output format for PR comment
- Suggested interactive section: `<title>`
  - Concept supported: `<concept>`
  - Why interactivity helps: `<learning value>`
  - Suggested implementation direction: `<plot/widget idea>`
  - Suggested location in notebook: `<where to insert>`

If notebook interactivity is already strong for all major concepts, post: `Interactivity review passed: no high-impact additions identified.`
