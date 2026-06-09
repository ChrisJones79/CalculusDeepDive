# Chapter PR Agent Workflow

This repository uses a PR-centered multi-agent loop for chapter development in `NLPDE/`.

## Agents
1. **Chapter Author Agent**
   - Creates or updates a chapter notebook from the chapter PDF.
   - Opens/updates the PR and applies agent feedback.
2. **Content Coverage Agent**
   - Uses the chapter PDF as source-of-truth context.
   - Verifies notebook concept coverage and reports missing concepts only.
3. **Interactivity Agent**
   - Uses the chapter PDF and notebook to propose high-impact visualization/interactivity additions.

## PR trigger
Workflow file: `.github/workflows/chapter-pr-agent-cycle.yml`

On PR updates affecting `NLPDE/**`, the workflow:
- Enforces a 1:1 chapter mapping by requiring exactly one changed PDF and one changed notebook in `NLPDE/`, with identical filenames before the extension (case-sensitive), e.g., `NLPDE/NLPDE_Ch2.pdf` ↔ `NLPDE/NLPDE_Ch2.ipynb`.
- Runs content coverage review stage.
- Runs interactivity review stage.
- Runs author revision-loop guidance stage.

## Preprocessing recommendation (shared chapter context)
Yes—preprocessing is recommended because multiple agents reuse the same chapter context.

Recommended pattern:
1. Extract chapter PDF text once in a preprocessing step.
2. Chunk by section/subsection with page metadata.
3. Create embeddings and index chunks in a vector store.
4. Expose retrieval output to each agent so all reviews use consistent chapter evidence.

This reduces repeated parsing costs, improves consistency across agent comments, and helps produce page/section-cited feedback.
