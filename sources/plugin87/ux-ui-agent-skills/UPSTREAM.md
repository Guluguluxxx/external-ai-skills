# plugin87/ux-ui-agent-skills

- Baseline: `f2e2f7fcc5cb9d99bbd8ec5e0d75cebb98e21e7e`
- Version: `2.8.0`
- License: MIT
- Mode: `pointer`
- Selected source: `.claude/skills/data-dashboard/SKILL.md`
- Adoption: adapted into `my-ai-skills/skills/adapted/personal-data-dashboard`.

## Why adapted

The upstream data-dashboard Skill is useful, but it assumes the surrounding repository exists: it calls `scripts/*.mjs`, points to `examples/*`, and inherits a broader Claude-specific design system. Installing only the Skill file would leave broken verification references; installing the whole kit globally would add unrelated opinions and context.

The personal adaptation keeps the durable dashboard-specific rules and delegates validation to the current project's actual tooling.
