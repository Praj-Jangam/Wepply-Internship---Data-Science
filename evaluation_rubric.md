# Week 4 Evaluation Rubric 

This rubric was designed for Week 4 to evaluate CV optimisation outputs across four dimensions:
**Keyword coverage (ATS relevance), Role relevance, Clarity, and Faithfulness (hallucination control)**.

---

## Scoring scale (0-2)

### A) Keyword coverage (ATS relevance) - 0 to 2
Measures whether the output reflects **JD keywords that are supported by the CV**.
- **2**: Covers most supported JD keywords (strong overlap) and uses them in a sensible way.
- **1**: Covers some supported JD keywords but misses obvious ones or stays generic.
- **0**: Misses most supported JD keywords or is largely irrelevant to the JD.

**Rule:** *Never reward “coverage” if the keyword is not supported by the CV.*

---

### B) Role relevance (tailoring quality) - 0 to 2
Measures whether the output is clearly tailored to the target role.
- **2**: Strong tailoring (language and suggestions match the role/level).
- **1**: Some tailoring but still partly generic.
- **0**: Not tailored / wrong direction.

---

### C) Clarity & readability - 0 to 2
Measures readability and structure.
- **2**: Clear, concise, properly structured (lists are readable; avoids filler text).
- **1**: Mostly readable but slightly repetitive or messy.
- **0**: Hard to read, overly long, or inconsistent structure.

---

### D) Faithfulness (hallucination control) - 0 to 2
Measures whether the output stays within CV facts.
- **2**: No invented tools/metrics/achievements; respects “CV-only facts”.
- **1**: Minor overreach (vague claims or a single unsupported tool/number).
- **0**: Clear hallucinations (multiple unsupported tools, metrics, or invented achievements).

---

## Binary checks (Yes/No)
- **Format OK**: parsed JSON exists and matches expected “single JSON object” output.
- **Constraints OK**: no unsupported tools/metrics introduced (strict).

---

## Suggested failure tags
- `wrong_format` - JSON invalid or missing
- `hallucination` - introduces unsupported tools/metrics/claims
- `missed_keywords` - weak ATS keyword coverage (supported keywords missing)
- `generic` - output is generic and not role/JD aligned
- `ok` - no major issues detected

---

## Total score
Total score = A + B + C + D (**/8**)

Date generated: 2026-02-18
