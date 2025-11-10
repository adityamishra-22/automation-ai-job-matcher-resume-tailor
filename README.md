# AI-Powered LinkedIn Job Matcher & Resume Tailor

This workflow automates your job search by scraping fresh **LinkedIn job listings**, parsing your resume, and using **Google Gemini AI** to generate:
- A structured job–resume match analysis
- A **match score (0–100)** with evidence
- A **custom cover letter**
- **Actionable resume improvement points**

It’s a complete AI-driven career assistant — directly integrated with Google Sheets for tracking and automation.

---

## 🚀 How It Works
1. **Trigger:** Manual or scheduled execution.
2. **Fetch Job Criteria:** Reads filters from a Google Sheet (`Filter` tab) — like keywords, location, experience level, and remote preference.
3. **Build LinkedIn Search URL:** Dynamically constructs a job search URL (e.g., `https://www.linkedin.com/jobs/search/...`).
4. **Scrape Job Listings:** Extracts job titles, companies, and links using HTML parsing nodes.
5. **Fetch Job Details:** Opens each job posting and extracts:
   - Title  
   - Company  
   - Location  
   - Description  
   - Job ID / Apply link  
6. **AI Resume Matching (Gemini):**
   - Compares your resume (downloaded from Google Drive) against each job.
   - Performs **job analysis** and **resume analysis**.
   - Scores job–resume match across 6 weighted categories.
   - Generates a **custom cover letter (150–220 words)**.
7. **Resume Improvement (Gemini Agent 2):**
   - Lists specific resume tweaks tagged as `[ADD]`, `[REMOVE]`, `[REWRITE]`, etc.
   - Outputs concise, actionable edits.
8. **Fresher Filter:** Flags jobs as “fresher friendly” based on title & description keywords.
9. **Output:** Logs everything to Google Sheets (`Result` tab):
   - Job Title, Company, Link, Cover Letter, Match Score, Core Skills, Improvement Tips, Fresher flag.

---

## 🧩 Tech Stack
n8n • Google Gemini (LLM) • Google Sheets API • Google Drive API • LinkedIn (public jobs HTML) • JavaScript

---


## 📈 Example Flow
[Google Drive Resume] ➜ [Get Job Filters] ➜ [LinkedIn URL Builder] ➜ [HTML Scraper] ➜ [Gemini AI Match + Cover Letter] ➜ [Resume Improvement Agent] ➜ [Google Sheets Log]


---

## 🧠 Output Sheet Schema
| Column | Description |
|--------|--------------|
| Title | Job title parsed from LinkedIn |
| Company | Employer name |
| Location | Job location |
| Link | Direct LinkedIn apply link |
| Cover Letter | Gemini-generated tailored letter |
| Score | Match score (0–100) |
| Skills | Extracted key resume skills |
| Improvements | AI-suggested resume edits |
| is_fresher_friendly | Yes/No flag for freshers |

---

## ⚙️ Setup
1. Import `AI-Powered LinkedIn Job Matcher & Resume Tailor.json` into your n8n instance.
2. Connect credentials:
   - Google Sheets (OAuth2)
   - Google Drive (OAuth2)
   - Google Gemini (PaLM API)
3. Update:
   - Resume file link in the “Download File” node.
   - Source and result Sheet IDs.
4. (Optional) Schedule it daily to auto-update job matches.

---

## 💡 Features
- **LLM-Powered Matching:** Scores jobs across 6 categories with evidence bullets.
- **Structured JSON Parsing:** Cleans Gemini output with custom brace counter for valid JSON.
- **Resume Tailor Agent:** Suggests exact resume improvements — no fluff.
- **Smart Filtering:** Detects “fresher friendly” roles.
- **Google Sheets Sync:** All results are stored neatly and auto-updated.

---

## 📸 Demo
<img width="1291" height="653" alt="image" src="https://github.com/user-attachments/assets/35dc548c-07fe-467e-b713-7146d4f9caaf" />


---

## 📄 License
MIT © 2025 Aditya
