# agentskills/agentskills

Reviewed as the canonical Agent Skills format reference.

## Decision

- Mode: pointer
- Use: reference only
- Runtime installation: no
- Reviewed commit: `69ef37e9424c0a7ea9dd2293b559e43ec8176379`

## What is adopted

The personal Skill lifecycle uses this source for portable-format checks:

- a Skill directory contains `SKILL.md`;
- YAML frontmatter includes required `name` and `description`;
- `name` follows the standard naming constraints and matches the directory;
- `description` explains both capability and activation context;
- `compatibility` records real environment requirements when needed;
- `metadata` remains string-to-string data;
- `allowed-tools` is experimental and is not treated as a universal authorization boundary;
- main instructions stay compact and detailed material moves to referenced files;
- relative references stay shallow;
- `skills-ref validate` may be used as format evidence.

## Boundary

This standard defines a portable Skill format. It does not replace:

- security review;
- source/provenance tracking;
- Base / New / Mine update policy;
- rollback and install verification;
- active Codex host compatibility checks.

Those remain owned by `personal-skill-lifecycle`.
