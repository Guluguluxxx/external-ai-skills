# mordor-forge/study-skill

- Upstream: https://github.com/mordor-forge/study-skill
- Baseline: `dffa35f955c421d65c326342b5273727906b26ee`
- Adoption: direct, project-local, on demand
- License status: README declares MIT, but no root LICENSE file was found during review; keep pointer-only and do not republish source.

## What it owns

A study workspace is durable state, independent of chat memory:

```text
.study-config.json
.fsrs/cards.json
lessons/
practice/
notes/
sources/        # when source material is extracted locally
```

`study init` also initializes a Git repository and the workflow commits lesson/session state.

Therefore use it only in a dedicated new study workspace. Do not initialize it at the root of an existing code repository or the main Obsidian Vault.

## Runtime dependencies

Core FSRS review:

- Go >= 1.22
- nested module: `scripts/fsrs`
- build the local FSRS binary before review features are expected to work

Optional book catalog:

- Python >= 3.11
- uv
- pydantic >= 2
- pdfplumber >= 0.11

The catalog is optional and should not be installed merely to use basic study sessions.

## Optional integrations

Do not automatically install:

- NotebookLM MCP
- SciAgent-Skills
- context7
- Playwright
- visual-explainer
- local RAG tools
- calibre/pandoc

NotebookLM MCP uses undocumented browser APIs/cookie authentication according to the upstream README and requires a separate security/account decision.

## Personal use boundary

Use this Skill only for explicit multi-session learning intent where structured lessons, exercises, resumable state, and spaced repetition are wanted.

Do not trigger it for:

- ordinary factual questions;
- one-off explanations/tutorials;
- normal coding implementation;
- personal Obsidian note capture.

Its teaching policy intentionally makes the user implement exercises. That is acceptable inside an explicit study workspace, but should not leak into normal development workflows.

## Risk

Medium.

Main surfaces:

- filesystem writes in the dedicated workspace;
- `git init` and frequent commits;
- compiled Go helper execution;
- optional Python dependency environment and book-directory scanning;
- optional external/network/account integrations.

## Update policy

Review Base → New before use.

Keep direct while the upstream remains compatible with dedicated-workspace scope. Create an adapted version only if its core teaching/session semantics or workspace boundaries conflict with the personal workflow.
