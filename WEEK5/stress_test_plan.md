# Stress-Test Plan (Week 5)

Goal: ensure the inference notebook/script is stable under realistic and worst-case inputs.

## What to stress-test
1) **Long CV text** (large bullet lists, long skills list)
2) **Long JD text** (multiple sections + many requirements)
3) **Missing JD** (for tasks where JD is optional)
4) **Noisy CV** (typos, inconsistent casing, weird formatting)
5) **Edge constraints** (tight max tokens, strict JSON-only)

## Recommended test runs
### A) Baseline run (sanity)
- Model: TinyLlama (or your chosen demo model)
- max_new_tokens: 420
- retry_tokens: 320
- Run on: `eval_prompts_v1.json` (25 cases)
- Record: JSON parse success rate, time per case

### B) Edge-case run
- Run on: `edge_case_eval_prompts_v1.json` (25 cases)
- Record:
  - JSON parse success rate
  - Most common failure tags (wrong_format / hallucination / generic / missed_keywords)

### C) Stress max length
- Pick 3 cases with the longest CV/JD
- Increase max_new_tokens to 700
- Ensure runtime stays stable and output stays JSON-only

## What to capture in notes
- GPU type (if Colab), VRAM usage (approx)
- tokens settings used
- parse success counts (e.g., 24/25)
- any crash / OOM messages
- examples of bad formatting and how the repair retry helped

## Quick pass criteria
- Notebook runs end-to-end without crashes
- Output JSON saved successfully
- Parse rate ≥ 85% on baseline, ≥ 75% on edge-case set (small-model realistic)
