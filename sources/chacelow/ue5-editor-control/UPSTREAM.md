# chacelow/ue5-editor-control

- Baseline: `3d02952714877c8b67feba86649e9e206522d1fa`
- License: MIT
- Mode: `pointer`
- Compatibility claimed upstream: UE5 5.4+, tested with UE5.7
- Adoption: adapted experimental policy; plugin remains upstream.

## Security posture

Direct source review of `HttpCommandServer.cpp` found no authentication check in the request handlers and permissive `Access-Control-Allow-Origin: *` responses. The plugin exposes high-impact editor commands, including generic reflection and `execute_python`.

The reviewed installer also deletes an existing plugin directory and downloads/extracts a GitHub Release ZIP without checksum/signature verification.

Treat port 58080 as a trusted-local control surface. Do not expose it beyond the local trusted machine/network boundary.

## Installation posture

Do not use the reviewed `install.sh` blindly in a production project.

First validation must use a disposable/copy UE5.7 project. Pin the plugin/release, record the downloaded artifact hash, then test read-only commands before write commands.

The prebuilt plugin route does not require converting a Blueprint project to a C++ project. The source-build fallback should not be used unless compilation is intentionally accepted.
