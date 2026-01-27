# Wepply Internship - Data-Science

# CV Optimizer LLM 

This project builds a low-cost CV optimization system using an open-source LLM (DeepSeek-7B + QLoRA).  
The goal is to improve CV content for a specific job description while keeping everything truthful and ATS-friendly.

## What the tool does (in simple words)
You paste a CV section + a job description, and the model returns:
- improved CV bullets and/or summary
- job-relevant keywords used
- warnings if important info is missing (instead of inventing details)

## CV Optimization Use Cases 

### 1) Bullet Rewriting (Clarity + Impact)
**Goal:** Rewrite CV bullet points so they sound professional, clear, and results-focused.  
**Input:** CV bullets (experience/projects).  
**Output:** Improved bullets with strong action verbs and clear outcomes.  
**Rule:** Do not change meaning or add new facts.

### 2) ATS Keyword Optimization (Without Lying)
**Goal:** Make the CV more ATS-friendly by using job keywords naturally.  
**Input:** CV text + job description.  
**Output:** Updated bullets/summary that include relevant keywords.  
**Rule:** Only use skills/tools that already exist in the CV (no invented tools/experience).

### 3) Job Description Matching (Tailored CV)
**Goal:** Tailor the CV content to match a specific role/job description.  
**Input:** CV + job description + target role.  
**Output:** Tailored summary + tailored bullets aligned to responsibilities.  
**Rule:** Keep CV accurate; if something is missing, suggest what to add instead of guessing.

## Hard Safety Rules
- The model must NOT invent: tools, technologies, companies, job titles, degrees, dates, or achievements.
- If metrics are missing (e.g., “improved by X%”), the model should add a suggestion in `warnings` rather than making up numbers.
- All dataset examples must be anonymised (no real names, emails, phone numbers, addresses).

## Output Format (JSON)
The model returns structured JSON:
- `optimized_summary` (string)
- `optimized_bullets` (list of strings)
- `keywords_used` (list of strings)
- `warnings` (list of strings)


