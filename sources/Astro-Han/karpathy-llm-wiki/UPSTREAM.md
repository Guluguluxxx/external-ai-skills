# Astro-Han/karpathy-llm-wiki

- Baseline: `eafcc77001e496cc43499e4923b663aec722c813`
- License: MIT
- Mode: `mirror`
- Adoption: direct, project-local, isolated experiment.

## Review

The runtime is self-contained: one `SKILL.md`, four templates, and one Python standard-library evidence checker. The checker is report-only.

The architecture intentionally owns `raw/` and `wiki/`. Do not point it at the root of an existing Obsidian Vault on first use. Create a separate project/topic directory and evaluate ingest → query → lint before deciding whether to integrate the resulting Markdown into a broader Vault.
