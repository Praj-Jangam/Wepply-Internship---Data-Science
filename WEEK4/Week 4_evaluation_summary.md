# Week 4 Evaluation Summary 

---

## Results snapshot
- **Parsed JSON pass rate (Format OK):** 96.0% (24/25)
- **Constraints OK rate (strict):** 58.3% (among parsed cases)
- **Average total score:** 6.04/8 (among parsed cases)

### Average score by task (parsed cases)
- **bullet_rewrite**: 7.14/8
- **jd_match**: 6.70/8
- **ats_optimize**: 4.00/8

---

## Common failure patterns (from outputs)
Top failure tags (all cases):
- **ok**: 12
- **hallucination**: 10
- **missed_keywords**: 2
- **wrong_format**: 1

What this suggests:
- **wrong_format**: occasional JSON formatting failure (small model behaviour).
- **hallucination**: when present, mostly “unsupported tools/metrics” injection.
- **missed_keywords / generic**: outputs that don’t strongly reflect supported JD keywords.

---

## Suggested data & prompt improvements 
1) **Add more “CV-only facts” negatives**  
   Include training examples where the correct output explicitly warns: “JD requests X, but CV doesn’t support it, so not added.”

2) **Force supported-JD keyword grounding**  
   For `ats_keywords` and `jd_match`, add instruction line:  
   “Extract keywords from JD, then keep only those supported by CV evidence.”

3) **Tighten output length & structure**  
   Short, consistent strings reduce format drift. Keep list items < 1–2 lines where possible.

4) **Add schema-validation training examples**  
   Ensure arrays contain strings only; avoid nested objects in `warnings` and `matches`.

5) **Broaden coverage of near-duplicate JDs**  
   Add multiple JDs per role family so the model learns stable patterns (KPI reporting, validation, stakeholder updates, etc.).

---

