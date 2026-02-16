# Dataset validation report (Week 2)

Source training file: cv_train_v0.jsonl (note: file contained multiple JSON arrays concatenated; parsed successfully into 522 raw records).
Duplicates removed by original id: 22 duplicates removed, leaving 500 unique records.

## v1 training dataset summary

Total records: 500
Task counts:
- bullet_rewrite: 208
- jd_match: 177
- ats_keywords: 115

JD conditioning checks:
- jd_match records with empty JD: 0
- ats_keywords records with empty JD: 0

Schema checks:
- Missing required top-level keys: 0
- v1 id unique: True
- jd-conditioned tasks missing required instruction lines: 0

## v2 evaluation prompt set summary

Total eval prompts: 25
- jd_match: 11
- ats_keywords: 7
- bullet_rewrite: 7
- Eval jd_match/ats_keywords with empty JD: 0
