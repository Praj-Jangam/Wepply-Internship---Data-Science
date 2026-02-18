# CV Optimisation — Week 3 Inference Demo

This repository contains a lightweight, reproducible inference demo for CV optimisation tasks using a Hugging Face model and a fixed evaluation prompt set.

## What’s included
- **Evaluation prompts**: `eval/eval_prompts_v2.json` (25 cases)
- **Inference script**: `src/run_inference.py`
- **Example prompts**: `prompt_examples.md`
- **Outputs**: `outputs/` (generated)

## Tasks supported
- `bullet_rewrite` — rewrite experience bullets (no invented metrics/tools)
- `ats_keywords` — extract ATS keywords *from the JD* but keep only those supported by the CV
- `jd_match` — Matches / Gaps / Suggestions using the JD as source of truth
- `summary_rewrite` — short summary + key skills (CV-only)

---

## How to run (Colab)
1) Open your Colab notebook.
2) Upload `eval/eval_prompts_v2.json` to the Colab Files panel.
3) Install dependencies:
   - `pip install -r requirements.txt`
4) Run inference (either from the notebook or by copying the script logic).
5) Outputs will be saved as JSON (example: `outputs/eval_outputs.json`).

> Note: For public models you **do not** need a HF token. If you see warnings about `HF_TOKEN`, they’re about rate limits/speed only.

---

## How to run (local)
```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt

python src/run_inference.py \
  --eval eval/eval_prompts_v2.json \
  --out outputs/eval_outputs.json \
  --model TinyLlama/TinyLlama-1.1B-Chat-v1.0
```

---

## Example output format
Each eval case produces one result item:

```json
{
  "eval_id": "eval_001",
  "task": "jd_match",
  "model_output": "raw model text (may include extra text)",
  "parsed_json": {
    "matches": ["..."],
    "gaps": ["..."],
    "suggestions": ["..."],
    "warnings": ["..."]
  },
  "notes": null
}
```

- `parsed_json` is `null` when parsing fails.
- `notes` contains the parse error (if any).

---

## Reproducibility checklist
- Keep evaluation prompts versioned (e.g., `eval_prompts_v2.json`).
- Save outputs under `outputs/` and commit only the latest run if needed.
- Pin dependencies in `requirements.txt`.
