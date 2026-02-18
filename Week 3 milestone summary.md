# Week 3 milestone summary (Person B — Data / Dev Lead)

## Deliverables shipped
- **Colab inference demo**: notebook runs inference over the eval prompt set and saves outputs.
- **Example CV optimisation prompts**: documented in `prompt_examples.md`.
- **User-facing README**: includes how to run + expected output format.
- **Reproducible repo assets**: `requirements.txt` + `src/run_inference.py`.

## What works end-to-end
- Loads `eval/eval_prompts_v2.json` (25 cases)
- Runs inference with a lightweight Hugging Face model
- Extracts/repairs JSON outputs (best-effort)
- Saves results to `outputs/eval_outputs.json`

## Notes / limitations
- Demo prioritises reproducibility over model quality (small model = occasional formatting failures).
- JSON parsing is best-effort; a “repair retry” is used to convert near-JSON outputs into valid JSON.

## Next steps (Week 4 ideas)
- Add schema validation (strings-only lists) + strict enforcement
- Add scoring rubric + comparison across prompt versions
- Swap to a stronger instruction model for higher-quality outputs
