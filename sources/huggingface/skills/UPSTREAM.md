# huggingface/skills

- Baseline: `80f9fa530e46f4ae642fcb9e1725bad0e1979395`
- License: Apache-2.0
- Mode: `mirror`
- Selected: `hf-cli`, `huggingface-local-models`, `huggingface-tool-builder`, `huggingface-gradio`

## Adoption

The upstream files remain mirrored unchanged, but `hf-cli` has a personal adapted version for safer global use.

- **hf-cli** — use the adapted personal version globally. Keep the mirrored upstream copy only as the Base for updates; its trigger is intentionally broad and its CLI can perform high-impact remote actions.
- **huggingface-local-models** — direct on demand for local GGUF/llama.cpp work.
- **huggingface-tool-builder** — direct on demand for reusable HF API scripts; generated scripts still require review.
- **huggingface-gradio** — direct project-local for Gradio projects.

External writes, destructive Hub actions, token disclosure, and paid Jobs/Endpoints remain outside autonomous read/research behavior.
