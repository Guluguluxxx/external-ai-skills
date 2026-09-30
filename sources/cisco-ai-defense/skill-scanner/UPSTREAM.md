# cisco-ai-defense/skill-scanner

- Stable reviewed release: `2.1.0`
- Reviewed commit: `a24df340ca6056a6446a239f4a7b114b11c6073a`
- Tracking branch at review: `main` @ `877a41320066cdee172095356c6818208ba7a806`
- License: Apache-2.0
- Adoption: tool-only, high-risk second opinion.

## Why stable release instead of main

The current main branch contains later scanner/LLM/CEL work that was not part of the latest published wheel at review time.

Use the signed 2.1.0 release for the local tool. Review a later release before upgrading.

## Default posture

Use the core/default scanner only.

Do not enable LLM, AI Defense, VirusTotal uploads, provider extras, meta-analysis, or other network-bearing modes by default.

A clean result is evidence, not a safety certificate.
