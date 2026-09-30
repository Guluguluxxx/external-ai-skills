# vercel-labs/skills

- Baseline: `3694740352eeef5cdd689af694c485f1ff62eec3`
- License: MIT
- Mode: `pointer`
- Adoption: tool-only.

Use as the common Skill transport/manager, not as the authority for whether an upstream update should enter a personal adapted Skill.

Preferred roles:

- `list` / `add --list`: discovery
- `use`: temporary low-frequency usage
- `add`: install a reviewed direct/adapted Skill
- `list`: inspect installed state
- `remove`: controlled uninstall
- `update`: only when the lifecycle policy says direct upstream update is acceptable

For adapted Skills, continue Base / New / Mine review rather than blindly applying upstream updates.
