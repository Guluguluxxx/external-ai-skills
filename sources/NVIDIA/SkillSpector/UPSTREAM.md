# NVIDIA/SkillSpector

- Upstream: https://github.com/NVIDIA/SkillSpector
- Baseline: `2226747e4ca97198bb82faf5085b8a75f2e1dc02`
- Package version at review: `2.12.0`
- License: Apache-2.0
- Mode: `pointer`
- Adoption: CLI/tool only; do not install the bundled `skill-inspector` Skill.

## Why tool-only

The bundled `skills/skill-inspector/SKILL.md` overlaps heavily with the personal `personal-skill-lifecycle` Skill. Keep one canonical decision workflow and use SkillSpector as a scanner that supplies static evidence.

## Default use

Prefer static scanning first:

```bash
skillspector scan <TARGET> --no-llm
```

Manual semantic review remains mandatory.

Optional LLM mode may send analyzed content to a configured provider and requires separate credential/provider review.

## Installation policy

Pin installation to the reviewed commit rather than following a moving branch:

```bash
uv tool install git+https://github.com/NVIDIA/skillspector.git@2226747e4ca97198bb82faf5085b8a75f2e1dc02
```

MCP extra is not part of the default setup.
