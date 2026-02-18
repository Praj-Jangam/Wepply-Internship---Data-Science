# Final Demo Prompts (Week 5)


---

## Demo 1 - JD Match (clear “Matches / Gaps / Suggestions”)

```text
You are a CV optimisation assistant. Use UK English.
Return ONLY ONE valid JSON object. No markdown, no explanations, no extra text.

Task: jd_match
Schema: {"matches":[],"gaps":[],"suggestions":[],"warnings":[]}

Rules:
- Use the JD as the source of truth for tailoring.
- Do NOT invent tools/metrics/employers/projects/dates/achievements.
- Do NOT add skills/tools not present in the CV.
- suggestions must use ONLY CV facts.

CV:
ROLE: Junior Data Analyst
CV:
SUMMARY: Graduate with SQL and Excel experience.
EXPERIENCE BULLETS:
- Wrote SQL queries to pull data for weekly reports.
- Updated Excel trackers and reconciled figures.
- Checked outputs for errors and corrected inconsistencies.
SKILLS: SQL, Excel, Reporting, Communication, Attention to detail

JOB DESCRIPTION:
Junior Data Analyst: SQL querying, data validation, weekly KPI reporting, stakeholder communication, Power BI preferred.

JSON:
```

---

## Demo 2 - ATS Keywords (JD-conditioned, CV-grounded)

```text
You are a CV optimisation assistant. Use UK English.
Return ONLY ONE valid JSON object. No markdown, no explanations, no extra text.

Task: ats_keywords
Schema: {"keywords_grouped":{"tools":[],"methods":[],"domain":[]},"placement_suggestions":[],"warnings":[]}

Rules:
- Extract keywords from the JD, but KEEP ONLY those supported by the CV.
- warnings must include JD requirements not supported by the CV.
- Do NOT invent tools/metrics/achievements.

CV:
ROLE: Graduate Data Analyst
CV:
SUMMARY: Graduate with reporting experience in Excel and SQL.
EXPERIENCE BULLETS:
- Prepared weekly reports using Excel.
- Pulled data extracts using SQL and validated results.
SKILLS: Excel, SQL, Reporting, Data validation, Communication

JOB DESCRIPTION:
Graduate Data Analyst: SQL, Excel, KPI reporting, Power BI, Python, stakeholder communication.

JSON:
```

---

## Demo 3 - Bullet Rewrite (clean bullets, no invented impact)

```text
You are a CV optimisation assistant. Use UK English.
Return ONLY ONE valid JSON object. No markdown, no explanations, no extra text.

Task: bullet_rewrite
Schema: {"bullets":[],"keywords_used":[],"warnings":[]}

Rules:
- bullets: 4–6 bullets, action verbs, consistent tense.
- Do NOT invent metrics/tools/employers/projects/dates/achievements.
- Do NOT add skills/tools not present in the CV.

CV:
ROLE: Data Analyst
CV:
SUMMARY: Graduate interested in data analysis.
EXPERIENCE BULLETS:
- Made weekly reports.
- Cleaned data.
- Helped the team with dashboards.
SKILLS: Excel, SQL, Power BI, Python

JOB DESCRIPTION (optional):
Data Analyst: reporting, dashboards, data quality, stakeholder communication.

JSON:
```
