# vercel-labs/skills

- Baseline commit: `3694740352eeef5cdd689af694c485f1ff62eec3`
- Reviewed package: `skills@1.7.0`
- Node engine: `>=22.20.0`
- License: MIT
- Mode: `pointer`
- Adoption: tool-only transport/installer.

## Responsibility boundary

`vercel-labs/skills` is not the trust or update authority.

```text
personal-skill-lifecycle
→ audit / direct-adapt-reject / provenance / Base-New-Mine / backup / verification

vercel-labs/skills
→ discover / materialize / install / symlink-copy / list / controlled removal
```

## Important reviewed behavior

### Agent-context auto confirmation

When the CLI detects that it is running inside an AI Agent:

- `add` automatically enables non-interactive yes mode;
- `remove` automatically enables non-interactive yes mode.

Therefore CLI prompts are not a sufficient safety boundary when Codex invokes the tool. Personal lifecycle rules must remain the authorization layer.

### Temporary use

`skills use` downloads/materializes a selected Skill and injects its `SKILL.md` into a generated prompt or launches a supported agent with that prompt.

It avoids permanent installation, but it does **not** avoid executing untrusted instructions.

Use it only after the candidate has reached an acceptable review level.

### Telemetry and audit network calls

Telemetry is enabled by default unless `DO_NOT_TRACK` or `DISABLE_TELEMETRY` is set.

Reviewed endpoints:

- `https://add-skill.vercel.sh/t`
- `https://add-skill.vercel.sh/audit`

Install telemetry can include source identifier, selected Skill names, target agents, install URL and related install metadata.

The personal default is to run this tool with telemetry disabled. SkillSpector/Cisco/manual review remain the security evidence path.

### Installation and lock state

The tool can:

- clone/download remote sources;
- install into canonical/project/global Skill locations;
- use symlinks or copies;
- write local/global Skill lock files;
- update or remove installed state.

It includes path sanitization and several safeguards, but mutation still requires lifecycle backup/verification.

## Preferred use

Do not globally install a floating CLI version.

Use the reviewed package on demand, for example with a version-pinned `npx skills@1.7.0 ...` invocation, after confirming Node compatibility.

For Skill sources, use exact reviewed commit/path when permanence or reproducibility matters.

## Command policy

Preferred:

- `list` / `add --list` — discovery after source is identified;
- `use` — reviewed low-frequency Skill without permanent install;
- `add` — transport for already-reviewed canonical source;
- `list` — inspect deployment state.

Restricted:

- `remove` — lifecycle mutation; backup/intent required;
- `update` — allowed only when lifecycle policy has already decided the update is acceptable;
- `--all` / wildcard bulk operations — avoid in autonomous personal workflows.

For adapted Skills, never replace Base/New/Mine with `skills update`.
