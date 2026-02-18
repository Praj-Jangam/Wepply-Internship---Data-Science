# CV Optimiser LLM (DeepSeek-7B + QLoRA) — Reproducible Demo

Low-cost CV optimisation using an open-source LLM fine-tuned with QLoRA.
Given a **CV snippet** and (optionally/usually) a **job description**, the system returns **ATS-aware**, **truthful** improvements in **structured JSON**.

This README merges the previous versions into a single, handover-friendly entry point.

---

## What the tool does
You paste a CV section + a job description (JD), and the model returns:
- improved CV bullets and/or summary
- job-relevant keywords used (CV-grounded)
- warnings for missing info instead of inventing facts

---

## Supported tasks
- `bullet_rewrite` — rewrite experience bullets (no invented metrics/tools)
- `ats_keywords` — extract keywords **from the JD** but keep only those **supported by the CV**
- `jd_match` — **Matches / Gaps / Suggestions** using the JD as source of truth
- `summary_rewrite` — short summary + key skills (CV-only)

---

## Hard safety rules (non-negotiable)
- Do **NOT** invent: tools, technologies, companies, job titles, degrees, dates, metrics, or achievements.
- If metrics are missing (e.g., “improved by X%”), add a suggestion in `warnings` rather than making up numbers.
- Dataset examples should be anonymised (no real names, emails, phone numbers, addresses).

---

## Repository structure (recommended)
```
cv-optimiser-llm/
├─ README.md
├─ requirements.txt
├─ notebooks/                 # colab notebooks (baseline, finetune, demo)
├─ src/                       # scripts (inference, json parsing, eval)
├─ data/
│  ├─ train/                  # cv_train_v0/v1
│  └─ eval/                   # eval prompts + edge cases
├─ prompts/                   # prompt templates + final demo prompts
├─ reports/                   # evaluation rubric/results + milestone summaries
└─ outputs/                   # generated outputs (usually gitignored)
```

---

## Quickstart (local)
```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt

python src/run_inference.py \
  --eval data/eval/eval_prompts_v1.json \
  --out outputs/eval_outputs.json \
  --model TinyLlama/TinyLlama-1.1B-Chat-v1.0
```

> Notes  
> - `TinyLlama` is fine for a **demo baseline**. For the main project model, use **DeepSeek-7B base** or **DeepSeek-7B + QLoRA adapter** (see notebooks).  
> - A Hugging Face token (`HF_TOKEN`) is optional for public models; it only improves download speed/rate limits.

---

## Quickstart (Colab)
1) Open the Colab inference notebook (see `notebooks/`).
2) Upload your eval file (e.g., `data/eval/eval_prompts_v1.json`) to the Colab Files panel.
3) Install deps:
   - `pip install -r requirements.txt`
4) Run inference.
5) Outputs save to `outputs/eval_outputs.json`.

---

## Inputs
### Evaluation prompts
- `data/eval/eval_prompts_v1.json` (main 20–30 case set)
- `data/eval/edge_case_eval_prompts_v1.json` (stress testing)

---

## Output format (example)
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
- The script uses a **repair retry** to convert near-JSON into valid JSON when needed.

---

## Prompt templates & demo prompts
- `prompts/prompt_templates_v2.md` — stable JSON templates
- `prompts/prompt_examples.md` — copy/paste examples
- `prompts/final_demo_prompts.md` — polished prompts for live demo

---

## Stress testing
See `reports/stress_test_checklist.md` for test runs and pass criteria.

---

## Troubleshooting
### HF_TOKEN warning
If you see warnings about `HF_TOKEN`, it’s about rate limits/speed only for public models.

### Colab download interruptions
If downloads fail due to session interruption:
- Zip files first, then download one zip
- Or copy outputs to Google Drive and download from Drive

---

## License
Add your chosen license (MIT/Apache-2.0/etc.) in `LICENSE`.

_Last updated: 2026-02-18_
