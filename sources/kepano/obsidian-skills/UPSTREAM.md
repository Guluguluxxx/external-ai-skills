# kepano/obsidian-skills

- Upstream: https://github.com/kepano/obsidian-skills
- Baseline: `3ccff5338ea700537839b21900aa5358a0402c98`
- License: MIT
- Mode: `mirror`
- Selected: `obsidian-markdown`, `obsidian-cli`
- Adoption: direct upstream use; no adapted fork currently required.

## Audit summary

### obsidian-markdown

Low risk. Pure Obsidian Markdown syntax guidance and reference files. No scripts, credentials, network actions, or external writes are bundled in the selected Skill.

### obsidian-cli

Medium risk because the Skill exposes commands that can read/write a Vault and can run Obsidian app-context JavaScript through `obsidian eval`. The selected Skill itself is Markdown-only and does not bundle an installer or credential store.

Use personal workflow rules to decide *whether* to write, what note format to use, and when confirmation is required. Keep this upstream Skill unchanged as the execution/syntax layer.

## Update rule

Mirror upstream bytes only after reviewing the Base → New diff. If future upstream behavior conflicts with personal workflow, create an adapted Skill in `my-ai-skills` instead of editing this mirror.
