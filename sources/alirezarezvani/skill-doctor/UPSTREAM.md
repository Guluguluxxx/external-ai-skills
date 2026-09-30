# alirezarezvani/claude-skills — skill-doctor

Reviewed baseline:

```text
repo: alirezarezvani/claude-skills
commit: 19392f7a08264ed00486a251f5b2098321771f94
path: engineering/skill-doctor/skills/skill-doctor
license: MIT
```

## Decision

Adapt, do not install directly.

The useful core is the evidence loop:

```text
recent real sessions
→ condensed/redacted transcript
→ rubric-anchored diagnosis
→ evidence-traced proposed diff
→ deterministic aggregation gate
→ human review
```

## Required personal changes

1. Treat the upstream letter grade / composite score as diagnostic presentation only.
2. Never change a Skill merely to improve the score.
3. Require an observed instruction gap that would plausibly have prevented the failure.
4. Default to current-repo history with strict repo matching.
5. Do not scan global histories unless explicitly requested.
6. Reading session history requires explicit approval because transcripts may contain sensitive material.
7. Correct the privacy claim: local scripts perform no network upload, but semantic scoring is done by the active Agent and therefore follows its model/provider data boundary.
8. Approved edits flow through `personal-skill-lifecycle`; the doctor never writes canonical Skill files directly.
