# Week 2 changes summary

## What was done

- Normalised task taxonomy: `ats_optimize` → `ats_keywords` (training + eval).
- Standardised schema to v1: `id`, `task`, `metadata`, `instruction`, `input{cv_text, job_description}`, `output`.
- Converted nested boolean constraints into a consistent `instruction` text block (constraints preserved in `metadata.constraints`).
- Enforced JD-conditioned prompting rules for `jd_match` and `ats_keywords` (instruction includes: 'Use the Job Description…' and 'Do not add skills/tools…').
- Removed duplicate training records by original `id` (kept first occurrence).
- Produced v2 eval prompt set with the same schema + task taxonomy.

## Notes

- Your v0 outputs were consistent across tasks (summary/bullets/keywords/warnings). For Week 2, the v1 exporter adds task-specific structured fields while preserving the original content.
- For `jd_match`, v1 includes `matches` from `keywords_used` and leaves `gaps` empty (to avoid hallucinating missing skills). You can add labelled gaps in a future dataset version if you want true gap supervision.
