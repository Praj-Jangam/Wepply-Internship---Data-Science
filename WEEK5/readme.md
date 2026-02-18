# CV Optimisation — Reproducible Inference Demo (v2)

This repo provides a lightweight inference demo for CV optimisation tasks:
- bullet rewriting
- ATS keyword extraction (JD-conditioned)
- JD matching (Matches/Gaps/Suggestions)
- summary rewrite

## Quickstart (local)
```bash
pip install -r requirements.txt

python src/run_inference.py \
  --eval eval/eval_prompts_v1.json \
  --out outputs/eval_outputs.json \
  --model TinyLlama/TinyLlama-1.1B-Chat-v1.0
```

## Quickstart (Colab)
1) Upload `eval_prompts_v1.json` (or your edge-case set) to Colab.
2) Install: `pip install -r requirements.txt`
3) Run inference code (notebook or script).
4) Outputs saved to `outputs/eval_outputs.json`

### Hugging Face token warning
If you see a warning about `HF_TOKEN`, it’s optional for public models.  
Adding a token improves download speed and rate limits.

## Prompt templates
See:
- `prompt_templates_v2.md` (stable JSON templates)
- `prompt_examples.md` (copy/paste examples)

## Stress testing
See `stress_test_checklist.md` for a checklist and pass criteria.

## Troubleshooting
### JSON parsing failures
- Small models sometimes add extra text or code fences.
- The script uses a **repair retry** to convert near-JSON into valid JSON.

### Downloads in Colab
If Colab downloads fail due to session interruption:
- Zip files first, then download one zip
- Or copy to Google Drive and download from Drive
