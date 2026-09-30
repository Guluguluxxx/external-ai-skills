# znyupup/ai-video-editing-skill

- Baseline: `b6429ab550a64c595dc68d42c47cf2b489a50619`
- License: MIT
- Mode: `pointer`
- Upstream Skill name: `vlog-auto-edit`
- Declared version: `1.1.0`
- Adoption: adapted into `personal-video-batch-editing`

## What is useful

The strongest reusable material is the deterministic FFmpeg/QC layer:

- inspect media before processing;
- validate a short sample before a large render;
- normalize output encoding deliberately;
- check audio/video duration drift and later-section sync;
- avoid unnecessary repeated re-encoding;
- explicitly preserve audio when overlaying video;
- do not use `-shortest` when it can truncate intended audio;
- generate thumbnails/storyboards/QC frames for review.

## What is not adopted as default behavior

The upstream workflow is optimized for travel Vlogs and assumes a much heavier AI stack.

Do not inherit these defaults automatically:

- `pip install` into the user's environment;
- Whisper/FunASR model downloads;
- visual-frame upload to external APIs;
- yt-dlp reference-video downloading;
- fixed "golden" shot lengths/content ratios/three-act rules;
- automatic BGM generation/services;
- shell-string FFmpeg execution.

These may be enabled only for an explicit AI-assisted editorial-analysis task.

## Security and data boundary

Local FFmpeg processing is preferred.

If visual API analysis is enabled later, extracted frames are user media and must be treated as data leaving the machine. API provider, endpoint, retention/privacy assumptions, and credential handling must be explicit before upload.

API keys must never be embedded in Skill source, GitHub, generated plans, or logs.

## Personal fit

The adapted personal workflow focuses on repeatable production operations:

```text
table / CSV
→ resolve source files
→ validate ranges
→ dry-run manifest
→ short sample
→ batch trim / encode / rename
→ media QC
→ report
```

AI transcription/vision/storytelling remains an optional separate layer instead of a prerequisite.

## Update policy

Review Base → New before importing upstream changes.

Prefer importing concrete FFmpeg correctness fixes and validation checks. Do not automatically import new cloud services, model dependencies, account integrations, or Vlog-specific editorial doctrine.
