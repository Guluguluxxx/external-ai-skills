# jokance/ue-ai-semantic-bridges

- Baseline: `0a8dffb40cf811e9ed3d47ddebd8455cec4341b9`
- Mode: `pointer`
- Root license file found: no
- Selected Skills: `ue-material-creator`, `ue-widget-creator`
- Adoption: research / project-local / direct if validated

## What this repository contains

The repository contains Agent Skills, DSL references, and launcher scripts for two separate Unreal Editor plugins:

- `MaterialSemanticBridge` from Fab
- `WidgetSemanticBridge` from Fab

The plugin implementations themselves are not present in this repository, so repository review cannot establish their full code-level security or write surface.

## Why this is lower privilege than UE5 Editor Control

The normal workflow is constrained:

```text
requirements
→ text DSL
→ validate / preview
→ review
→ single-file import
```

There is no general unauthenticated HTTP endpoint here for arbitrary editor commands. Persistent writes happen through the Bridge plugins' supported import surfaces rather than through arbitrary UObject reflection/Python execution.

This is lower privilege, not zero risk.

## Material workflow findings

- `validate` is read/diagnostic oriented.
- `normalize` validates, creates transient Unreal objects, exports canonical DSL, may render previews, and overwrites the input `.materialdsl` only after success.
- `import` writes the mapped `/Game` Material or MaterialInstanceConstant.
- `import-root` is a bulk write surface.
- `--build` is opt-in in the reviewed fixed launcher.
- The running-editor Windows wrapper defaults `MODE=import-root`; do not invoke it without an explicit safe mode.
- That wrapper may auto-launch Unreal Editor and contains a machine-specific `D:\Games\UE_5.7\...` fallback path.

## Widget workflow findings

- Normal flow is validate/preview first, then import.
- Persistent import writes the mapped Widget Blueprint.
- Documentation describes an `import-root` bulk path for the running-editor bridge.
- The reviewed docs reference `request_widgetsemantic_editor_windows.bat` and `request_widgetsemantic_editor_mac.sh`, but those files were not found at the documented repository paths in the reviewed commit.
- Treat that running-editor fallback as documentation/runtime drift until the actual installed package is verified.

## Installation boundary

Do not install either Skill into the global Codex Skill scope.

Before adoption:

1. Install/enable the corresponding Fab plugin in a disposable/copied UE5.7 project.
2. Verify the exact plugin version and Unreal compatibility locally.
3. Validate only first.
4. Preview generated output.
5. Test one new disposable asset import.
6. Demonstrate rollback.

Do not test batch `import-root` against a production project.

## Personal workflow boundary

- Prefer this semantic DSL path for new or structural Material/UMG authoring when the plugin is verified.
- Keep existing Custom-node-only HLSL logic changes as direct HLSL edits when the graph interface/structure does not need to change.
- Do not convert Blueprint projects to C++ merely for these workflows.
- Preview output is useful evidence, but final rendered/UMG appearance remains a human validation step.

## Update policy

Review Base → New before adoption or update.

Re-run the UE5.7 sandbox test when launcher behavior, DSL schema, import mapping, plugin baseline, bulk-import behavior, or preview semantics materially change.