# kepano/obsidian-skills

- Upstream: https://github.com/kepano/obsidian-skills
- Baseline: `3ccff5338ea700537839b21900aa5358a0402c98`
- License: MIT
- Mode: `mirror`
- Selected: `obsidian-markdown`, `obsidian-cli`

## Adoption

- `obsidian-markdown` → **direct**
- `obsidian-cli` → **adapted** in `Guluguluxxx/my-ai-skills/skills/adapted/obsidian-cli`
- personal note-routing / structure → **own** Skill `personal-knowledge-workflow`

## Audit summary

### obsidian-markdown

Low risk. Pure Obsidian Markdown syntax/reference guidance; no bundled scripts, credentials, network calls, or external-write tooling.

The mirrored files are preserved byte-identical to the reviewed upstream commit.

### obsidian-cli

Medium risk because the CLI can write/delete/move Vault files, publish content, change plugins/themes, and run Obsidian app-context JavaScript through `obsidian eval`.

The reviewed upstream Skill still uses the obsolete `silent` flag. Current official Obsidian CLI documentation says:

- installer version 1.12.7+ is required;
- **Command line interface** must be enabled in Settings → General;
- Obsidian must be running (or is launched by the first command);
- create/append-style commands are silent unless `open` is explicitly supplied;
- `open` and `overwrite` are current flags.

Therefore the upstream CLI mirror remains unchanged, while the personal adapted Skill carries current syntax and write-safety boundaries.

## Update rule

Review Base → New before syncing the mirror.

- Markdown-only compatible updates may remain direct.
- CLI changes must be compared against the adapted personal version.
- Do not overwrite personal write-routing or safety semantics from upstream.
