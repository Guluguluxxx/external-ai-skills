# MengTo/Skills

Reviewed as a design/visual workflow source, not as a runtime bundle.

## Baseline

```text
repo: MengTo/Skills
commit: 798db0a3ee4429ac8ed6bc5f4a59b6d45e7a914d
license: MIT
```

## Decision

Research + selective adaptation only.

### Useful transferable ideas

- turn references into explicit specs instead of vague style language;
- decompose visuals into layout/state/material/light/motion/interaction/performance layers;
- separate source facts from inferred implementation;
- preserve one owner for shared state such as camera/season/light;
- verify visual changes from real renders, not code descriptions;
- compare before/key/result from the same camera or viewport;
- keep visual evidence honest about capture method;
- change one or a small number of visual variables per iteration when isolating causes.

### Not adopted directly

The repository's 3D skills are mostly Three.js/WebGL implementations. Water, seasons, sky rays, virtual tours, VFX, and similar skills are useful as conceptual references but should not be installed into UE5.7 as execution instructions.

`workflow-score-to-target` is also not adopted as a general rule: numeric visual scores can be useful as communication aids, but they must not become the optimization target or override explicit acceptance criteria and human judgment.

## Personal integration

Renderer-neutral visual verification principles are incorporated into:

```text
Guluguluxxx/my-ai-skills
skills/own/universal-development-workflow/references/visual-verification.md
```
