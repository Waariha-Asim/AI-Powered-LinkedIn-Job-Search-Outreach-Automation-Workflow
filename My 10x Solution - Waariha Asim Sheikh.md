# My 10x Solution - Waariha Asim Sheikh

## The Problem

Manual job searching is time-consuming and inefficient. Finding relevant AI/ML opportunities on LinkedIn requires browsing through hundreds of posts daily, manually filtering by location, experience level, and role — then writing personalized emails or DMs for each opportunity. This process takes 2–3 hours every day, with no guarantee the jobs found are actually relevant.

## The 10x Claim

What previously took 2–3 hours of manual searching, filtering, and writing now runs automatically every night at 11 PM — zero manual effort required. The system discovers jobs, removes duplicates, filters for relevance using AI, and prepares personalized outreach drafts ready for human review and sending.

## My Solution

**AI-Powered LinkedIn Job Search & Outreach Automation** is an end-to-end human-in-the-loop AI automation built with n8n that:

- Scrapes LinkedIn job posts automatically using Apify
- Deduplicates posts to avoid processing the same opportunity twice
- Uses Groq LLM to evaluate each post for role, location, and experience fit
- Generates personalized email and LinkedIn DM drafts using Google Gemini
- Tracks everything in Google Sheets with status tracking
- Creates Gmail drafts for human review — AI prepares, human approves and sends

The workflow runs every night at 11 PM and processes both remote Pakistan opportunities and Karachi-based AI jobs (alternating daily to stay within free API limits).

## 5 Concepts Implemented

| # | Concept | Implementation |
|---|---|---|
| 1 | **Cron / Background Job** | Schedule Trigger fires at 11 PM daily — no manual intervention needed |
| 2 | **LLM Integration** | Groq (GPT-OSS-20B) filters job relevance; Google Gemini generates personalized email/DM drafts |
| 3 | **Web Scraping Pipeline** | Apify scrapes LinkedIn job posts for remote Pakistan and Karachi AI roles |
| 4 | **Database / Persistence** | Google Sheets stores all discovered jobs, AI drafts, match scores, and application statuses |
| 5 | **Email / Reporting** | Gmail API creates ready-to-review draft emails for each relevant opportunity |

**Swap note:** Web Scraping Pipeline replaces the standard "Caching logic" concept — caching did not fit this solution as job data changes daily and must always be fresh. Web scraping is an approved swap per the 10x Solution brief.

## Workflow Stages

| Stage | What Happens |
|---|---|
| 🔎 Discover | Apify scrapes LinkedIn for AI/ML job posts |
| 🧹 Deduplicate | Duplicate posts removed before LLM processing |
| 🧠 Filter | Groq evaluates role, location, and experience fit |
| ✍️ Personalize | Gemini creates tailored email and DM drafts |
| 📊 Track | Google Sheets logs all jobs, drafts, and statuses |
| 👤 Human Review | Gmail drafts reviewed and sent manually |

## Example Output

| Company | Role | Match Score | Type | Status |
|---|---|---|---|---|
| ARYtech | Associate AI Software Engineer | 9/10 | Email | Draft Ready |
| Maxtrone | AI/ML Engineer | 8/10 | Email | Draft Ready |
| Xperlabs | AI Engineer | 7/10 | LinkedIn DM | DM Ready |

## Tech Stack

| Component | Technology |
|---|---|
| Automation | n8n |
| Scraping | Apify |
| AI Filtering | Groq — GPT-OSS-20B |
| AI Drafting | Google Gemini |
| Data Tracking | Google Sheets |
| Email | Gmail API |

## How to Run

**Requirements:**
- n8n (self-hosted or cloud)
- Apify account (free tier)
- Groq API key (free tier)
- Gemini API key (free tier)
- Google Sheets OAuth
- Gmail OAuth

**Steps:**
1. Import `workflow.json` into n8n
2. Configure all API credentials in n8n
3. Connect Google Sheets and Gmail accounts
4. Set up target job search parameters in Apify tasks
5. Activate the workflow — it runs automatically at 11 PM daily

**Google Sheets columns:**
Date | Company | Role | Location | Experience | Match Score | Type | Contact Email | Author Name | Post URL | Apply Link | Email Draft | DM Draft | Status

## Human-in-the-Loop Design

This automation does not auto-send applications. The design is intentional:

> AI discovers → filters → drafts → human reviews → human sends

This keeps the workflow efficient while maintaining full control over every outreach message — no accidental applications sent.

## GitHub Repository

[https://github.com/Waariha-Asim/AI-Powered-LinkedIn-Job-Search-Outreach-Automation-Workflow](https://github.com/Waariha-Asim/AI-Powered-LinkedIn-Job-Search-Outreach-Automation-Workflow)

## Author

**Waariha Asim Sheikh**
AI Engineer | Generative AI | AI Automation
[GitHub](https://github.com/Waariha-Asim) · [LinkedIn](https://linkedin.com/in/waarihaasim)
