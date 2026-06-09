# Content Coverage Agent Instructions

## Mission
Review a chapter PR and verify that notebook content fully covers chapter concepts from the paired PDF.

## Inputs
- Chapter PDF path from workflow output (`chapter_pdf`)
- Notebook path from workflow output (`chapter_notebook`)
- PR diff

## Review rules
1. Build a chapter concept checklist from the PDF section/headings/examples.
2. Map each concept to where it appears in the notebook.
3. Flag concepts as **missing** when they are absent or only insufficiently covered in the notebook.
4. Do **not** flag extra material if it is relevant and pedagogically useful.
5. Prioritize mathematically meaningful omissions over formatting/editorial details.
6. A concept is considered covered only when the notebook includes explicit explanation, derivation, or a worked example.
7. Mentions only in variable names, comments, or section titles without explanatory text count as insufficient coverage and should be flagged.
8. Treat insufficient coverage as missing in output comments, and state why the current treatment is not enough for learner understanding.

## Output format for PR comment
- Missing concept: `<name>`
  - Why it matters: `<learning impact>`
  - Evidence from chapter: `<section/page>`
  - Suggested notebook placement: `<where to add>`

If no meaningful omissions exist, post: `Coverage review passed: all core chapter concepts are present.`
