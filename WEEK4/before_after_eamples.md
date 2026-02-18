# Before/After Examples (Week 4)
Selected: **3 strongest** + **3 weakest** (from 24 parsed cases).

---
## eval_001 - jd_match
**Total score:** 8/8 | **Tags:** ok | **Format OK:** Y | **Constraints OK:** Y

### CV (before)
```text
ROLE: Junior Data Analyst CV: SUMMARY: Graduate with SQL and Excel experience. EXPERIENCE BULLETS: - Wrote SQL queries to pull data for reports. - Updated Excel trackers. - Checked results for errors. SKILLS: SQL, Excel, Communication, Attention to detail
```
### Job Description
```text
Junior Data Analyst role: SQL querying, data validation, weekly KPI reporting, and stakeholder communication.
```
### Model output (after)
```json
{
  "matches": [
    {
      "name": "Graduate with SQL and Excel experience",
      "description": "Graduate with SQL and Excel experience. Wrote SQL queries to pull data for reports. Updated Excel trackers. Checked results for errors.",
      "skills": [
        "SQL",
        "Excel",
        "Communication",
        "Attention to detail"
      ]
    }
  ],
  "gaps": [],
  "suggestions": [
    {
      "name": "SQL querying",
      "description": "SQL querying to pull data for reports.",
      "skills": [
        "SQL"
      ]
    },
    {
      "name": "Excel trackers",
      "description": "Updated Excel trackers.",
      "skills": [
        "Excel",
        "Attention to detail"
      ]
    }
  ],
  "warnings": []
}
```
### Notes
- Missing supported JD keywords: analyst, junior

---
## eval_011 - jd_match
**Total score:** 8/8 | **Tags:** ok | **Format OK:** Y | **Constraints OK:** Y

### CV (before)
```text
ROLE: Reporting Assistant CV: SUMMARY: Graduate with Excel. EXPERIENCE BULLETS: - Updated production sheet. - Checked entries. - Shared weekly summary. SKILLS: Excel, Accuracy, Communication
```
### Job Description
```text
Reporting Assistant: Excel reporting, accuracy checks, weekly summaries, and clear updates to stakeholders.
```
### Model output (after)
```json
{
  "matches": [
    {
      "name": "ROLE",
      "description": "Reporting Assistant",
      "prompt": "What is your current role?"
    },
    {
      "name": "SUMMARY",
      "description": "Graduate with Excel",
      "prompt": "What are your skills in Excel?"
    },
    {
      "name": "EXPERIENCE BULLETS",
      "description": "Updated production sheet, checked entries, shared weekly summary",
      "prompt": "What specific tasks have you completed in your previous role?"
    },
    {
      "name": "SKILLS",
      "description": "Excel, Accuracy, Communication",
      "prompt": "What are your key skills in Excel?"
    }
  ],
  "gaps": [],
  "suggestions": [
    {
      "name": "EXPERIENCE BULLETS",
      "description": "Updated production sheet, checked entries, shared weekly summary",
      "prompt": "What specific tasks have you completed in your previous role?"
    },
    {
      "name": "SKILLS",
      "description": "Excel, Accuracy, Communication",
      "prompt": "What are your key skills in Excel?"
    }
  ],
  "warnings": []
}
```
### Notes
- No major issues detected by the heuristic checks.

---
## eval_012 - ats_optimize
**Total score:** 8/8 | **Tags:** ok | **Format OK:** Y | **Constraints OK:** Y

### CV (before)
```text
ROLE: Data Entry Assistant CV: SUMMARY: Graduate. EXPERIENCE BULLETS: - Entered data. - Checked details. - Filed documents. SKILLS: Accuracy, Attention to detail, Organisation
```
### Job Description
```text
Data Entry Assistant: accurate data entry, detail checks, and organised documentation management.
```
### Model output (after)
```json
{
  "keywords_grouped": {
    "tools": [],
    "methods": [],
    "domain": []
  },
  "placement_suggestions": [
    "Entry level"
  ],
  "warnings": [
    "Accuracy and attention to detail are required for this role. Please ensure that you accurately enter data and check details. Organised documentation management is also required."
  ]
}
```
### Notes
- Missing supported JD keywords: assistant

---
## eval_005 - ats_optimize
**Total score:** 2/8 | **Tags:** hallucination | **Format OK:** Y | **Constraints OK:** N

### CV (before)
```text
ROLE: Data Administrator CV: SUMMARY: Graduate. EXPERIENCE BULLETS: - Logged requests. - Updated records. - Filed documents. SKILLS: Documentation, Accuracy, Organisation
```
### Job Description
```text
Data Administrator: request logging, accurate record maintenance, documentation management, and audit-ready workflows.
```
### Model output (after)
```json
{
  "keywords_grouped": {
    "tools": [],
    "methods": [],
    "domain": []
  },
  "placement_suggestions": [
    "3-6 specific suggestions"
  ],
  "warnings": [
    "JD requirements that are not supported by the CV:",
    "1. Logged requests"
  ]
}
```
### Notes
- Missing supported JD keywords: administrator, data, documentation

---
## eval_016 - ats_optimize
**Total score:** 3/8 | **Tags:** hallucination | **Format OK:** Y | **Constraints OK:** N

### CV (before)
```text
ROLE: Junior Reporting Analyst CV: SUMMARY: Graduate with Excel. EXPERIENCE BULLETS: - Collected weekly figures. - Updated chart. - Shared summary. SKILLS: Excel, Communication, Organisation
```
### Job Description
```text
Junior Reporting Analyst: weekly reporting, chart updates, and concise summaries for stakeholders.
```
### Model output (after)
```json
{
  "keywords_grouped": {
    "tools": [],
    "methods": [],
    "domain": []
  },
  "placement_suggestions": [
    "3-6 specific suggestions"
  ],
  "warnings": [
    {
      "prompt": "JD requirements that are not supported by the CV",
      "warnings": [
        "Graduate with Excel"
      ]
    }
  ]
}
```
### Notes
- Missing supported JD keywords: analyst, chart, junior, reporting, weekly

---
## eval_002 - ats_optimize
**Total score:** 3/8 | **Tags:** hallucination | **Format OK:** Y | **Constraints OK:** N

### CV (before)
```text
ROLE: Data Quality Assistant CV: SUMMARY: Graduate. EXPERIENCE BULLETS: - Reviewed records. - Removed duplicates. - Corrected errors. SKILLS: Accuracy, Documentation, Attention to detail
```
### Job Description
```text
Data Quality Assistant: record review, duplicate removal, error correction, documentation, and maintaining clean reporting inputs.
```
### Model output (after)
```json
{
  "keywords_grouped": {
    "tools": [],
    "methods": [],
    "domain": []
  },
  "placement_suggestions": [
    "3-6 specific suggestions"
  ],
  "warnings": [
    {
      "rule": "JD requirement not supported by CV",
      "message": "Removed duplicate records"
    }
  ]
}
```
### Notes
- Missing supported JD keywords: assistant, data, documentation, quality

---
