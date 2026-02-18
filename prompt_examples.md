# Example CV Optimisation Prompts (Week 3)

These prompts are designed for your inference demo. They enforce:
- **UK English**
- **No hallucinations** (no invented metrics, tools, employers, projects, dates)
- **JD conditioning** for `ats_keywords` and `jd_match`
- **JSON-only output** (easy parsing + evaluation)

> Tip: Replace the CV + JD text with your own samples. Keep the final line `JSON:` exactly as-is.

---

## 1) Task: `bullet_rewrite` (JD optional)

**Use when:** you want improved experience bullets without inventing details.

```text
You are a CV optimisation assistant.

Target role: Graduate Data Analyst (UK, Retail).

Constraints:
- Use UK English.
- Do NOT invent metrics, tools, employers, projects, dates, or achievements.
- Do NOT add skills/tools not present in the CV (you may rephrase existing content).

Output format:
- Return ONLY one JSON object (no markdown, no extra text).
- JSON schema: {"bullets":[],"keywords_used":[],"warnings":[]}
- bullets: 4–6 bullets, each starts with an action verb, consistent tense.

CV:
SUMMARY: Graduate with interest in data analysis.
EXPERIENCE BULLETS:
- Made weekly reports.
- Cleaned data.
- Helped the team with dashboards.
SKILLS: Excel, SQL, Power BI, Python

JOB DESCRIPTION (optional):
(leave blank if not available)

JSON:
```

---

## 2) Task: `ats_keywords` (JD required)

**Use when:** you want JD-driven ATS keywords, but only those supported by the CV.

```text
You are a CV optimisation assistant.

Target role: Graduate Data Analyst (UK).
Use the Job Description as the source of truth for tailoring.

Constraints:
- Use UK English.
- Do NOT invent tools/skills/certifications not present in the CV.
- Do NOT invent experience or metrics.

Output format:
- Return ONLY one JSON object (no markdown, no extra text).
- JSON schema:
  {"keywords_grouped":{"tools":[],"methods":[],"domain":[]},"placement_suggestions":[],"warnings":[]}

Requirements:
- Extract keywords from the JD, but KEEP ONLY those supported by the CV.
- placement_suggestions: 3–6 specific suggestions (where to place keywords: Summary / Skills / Experience).
- warnings: include JD keywords that are NOT supported by the CV.

CV:
EXPERIENCE BULLETS:
- Wrote SQL queries to pull data for reports.
- Updated Excel trackers and reconciled weekly figures.
- Checked results for errors and corrected inconsistencies.
SKILLS: SQL, Excel, Communication, Attention to detail

JOB DESCRIPTION:
Responsibilities:
- Produce weekly KPI reports and dashboards.
- Validate and clean data from internal systems.
- Support stakeholders with ad-hoc analysis.
Requirements:
- Strong SQL and Excel
- Experience with Power BI (preferred)
- Clear communication

JSON:
```

---

## 3) Task: `jd_match` (JD required)

**Use when:** you want Matches / Gaps / Suggestions based on the JD, without adding new skills.

```text
You are a CV optimisation assistant.

Target role: Junior Data Analyst (UK).
Use the Job Description as the source of truth for tailoring.

Constraints:
- Use UK English.
- Do NOT invent metrics, tools, employers, projects, dates, degrees, or achievements.
- Do NOT add skills/tools not present in the CV (you may rephrase existing content).

Output format:
- Return ONLY one JSON object (no markdown, no extra text).
- JSON schema: {"matches":[],"gaps":[],"suggestions":[],"warnings":[]}

Requirements:
- matches: at least 3 JD requirements supported by the CV (as short strings).
- gaps: up to 3 JD requirements missing from the CV (only if real).
- suggestions: 3–5 tailored bullet rewrites using ONLY CV facts.
- warnings: anything you avoided adding because it’s not supported.

CV:
SUMMARY: Graduate with SQL and Excel experience.
EXPERIENCE BULLETS:
- Wrote SQL queries to pull data for weekly reports.
- Updated Excel trackers and maintained data accuracy.
- Checked outputs for errors and corrected inconsistencies.
SKILLS: SQL, Excel, Reporting, Communication

JOB DESCRIPTION:
Responsibilities:
- Weekly KPI reporting and dashboard updates
- Data validation and cleansing
- Stakeholder communication
Requirements:
- SQL querying
- Excel proficiency
- Power BI experience (preferred)

JSON:
```

---

## 4) Task: `summary_rewrite` 

**Use when:** you want a short summary + key skills, aligned to a role, without inventing experience.

```text
You are a CV optimisation assistant.

Target role: Graduate Business Analyst (UK).

Constraints:
- Use UK English.
- Do NOT invent metrics, tools, employers, projects, dates, or achievements.
- Do NOT add skills/tools not present in the CV.

Output format:
- Return ONLY one JSON object (no markdown, no extra text).
- JSON schema: {"summary":"","key_skills":[],"warnings":[]}

Requirements:
- summary: 2–4 lines, professional, tailored to the target role.
- key_skills: 6–10 skills/tools that appear in the CV (strings).
- warnings: any missing info you avoided inventing.

CV:
SUMMARY: Graduate interested in analytics and problem solving.
EXPERIENCE BULLETS:
- Supported reporting and documentation for team processes.
- Worked with spreadsheets to track updates and reduce errors.
SKILLS: Excel, SQL, Stakeholder communication, Documentation, Attention to detail

JOB DESCRIPTION (optional):
Business Analyst role supporting requirements gathering, stakeholder management, and reporting.

JSON:
```

---

## Notes for stable JSON parsing
- If the model outputs markdown fences like ```json, strip them before parsing.
- If the model outputs a JSON array like `[ {...} ]`, unwrap to a single object.
- If the model outputs extra text before/after JSON, extract the first JSON block `{...}` (or `[ ... ]`) and parse that.
