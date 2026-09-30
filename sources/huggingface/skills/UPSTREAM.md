# huggingface/skills

- Baseline: `80f9fa530e46f4ae642fcb9e1725bad0e1979395`
- License: Apache-2.0
- Mode: `mirror`
- Selected: `hf-cli`, `huggingface-local-models`, `huggingface-tool-builder`, `huggingface-gradio`

## Adoption

No personal fork is required at this baseline.

- **hf-cli** — direct on demand only. Do not keep globally active: its trigger is intentionally broad and the CLI can perform high-impact remote actions.
- **huggingface-local-models** — direct on demand for local GGUF/llama.cpp work.
- **huggingface-tool-builder** — direct on demand for reusable HF API scripts; generated scripts still require review.
- **huggingface-gradio** — direct project-local for Gradio projects.

External writes, destructive Hub actions, token disclosure, and paid Jobs/Endpoints remain outside autonomous read/research behavior.
