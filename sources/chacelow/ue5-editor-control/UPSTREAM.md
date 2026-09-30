# chacelow/ue5-editor-control

- Baseline: `3d02952714877c8b67feba86649e9e206522d1fa`
- License: MIT
- Mode: `pointer`
- Compatibility claimed upstream: UE5 5.4+, tested with UE5.7
- Adoption: adapted experimental policy; plugin remains upstream.

## Security posture

Direct source review found:

- `/api/execute` performs no authentication check;
- responses allow `Access-Control-Allow-Origin: *`;
- the plugin starts an HTTP listener on port 58080, but the reviewed plugin code does not explicitly enforce a loopback bind;
- `execute_python` compiles and executes arbitrary Python supplied through the request;
- `call_function` invokes a resolved UFunction through `ProcessEvent`; the exact-name execution path does not require Public/BlueprintCallable flags;
- generic reflection can write arbitrary object/component/asset properties and arrays;
- project/world settings can be changed and `save_all` persists dirty packages;
- actor deletion is performed directly through `World->DestroyActor`;
- reviewed mutation paths do not provide a general explicit transaction/Undo guarantee.

Treat the service as unauthenticated high-privilege editor control.

Verify the actual OS listener address before use. Do not assume "localhost" documentation proves loopback-only exposure.

## Installer posture

The reviewed `install.sh`:

- selects latest release unless a version is explicitly pinned;
- permits repository/download URL overrides;
- downloads a ZIP without checksum/signature verification;
- removes an existing `Plugins/UE5AIAssistant` directory before extraction.

Do not run it blindly against a production project.

Prefer a pinned reviewed artifact, record its SHA-256, and back up any previous plugin directory.

## Validation posture

First validation must use a disposable/copy UE5.7 project.

Test in privilege order:

```text
network/listener check
→ ping/commands
→ read-only actor/asset/level queries
→ inspect test Blueprint
→ create test Blueprint
→ bounded graph edit + compile
→ test Material
→ bounded Actor mutation
→ verify rollback
```

Do not exercise `execute_python`, generic `call_function`, settings writes, destructive commands, or `save_all` merely to prove availability.

The prebuilt plugin route does not require converting a Blueprint project to C++. Source-build fallback is opt-in only.

## Documentation drift

Current `AGENTS.md` describes 67 commands while the selected upstream `SKILL.md` metadata/overview still says 65. Treat the live reviewed command surface and source as authoritative.

## Update policy

Use Base / New / Mine review for every upstream change.

Any change to:

- HTTP binding/authentication;
- installer behavior;
- generic reflection / Python execution;
- command inventory;
- Blueprint graph behavior;
- persistence/transaction behavior

requires sandbox re-validation before promotion.
