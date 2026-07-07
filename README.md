🎓 TrackMate — AI-Powered Academic Risk Detection



\### 📌 Problem Statement



Students often show early warning signs of academic struggle — a sudden score drop, chronic low performance, or a slow decline — but these patterns can go unnoticed until it's too late. Manually reviewing every student's data isn't scalable.



🎯 Project Objective



Build an automated workflow that detects at-risk students from their academic data, classifies the type of risk using AI, and sends personalized, empathetic outreach — helping educators intervene early.



\---



🤖 How It Works



TrackMate is built entirely in \*\*n8n\*\*, using \*\*Google Gemini\*\* for AI classification.



1\. \*\*Trigger\*\* — Workflow starts (manual trigger for demo; swappable for a scheduled trigger in production)

2\. \*\*Read data\*\* — Pulls student records from Google Sheets (attendance, quiz scores, past averages, assignment status)

3\. \*\*AI classification\*\* — Gemini classifies each student into one of four categories:

&#x20;  - 🔴 `sudden` — a sharp, recent score drop

&#x20;  - 🟠 `chronic` — consistently low performance

&#x20;  - 🟡 `gradual` — slow, ongoing decline

&#x20;  - 🟢 `none` — no concerning pattern

4\. \*\*Parse response\*\* — extracts the AI's JSON output (risk type, reasoning, ready-to-send message)

5\. \*\*Route by risk type\*\* — a Switch node branches the workflow based on classification

6\. \*\*Send email\*\* — Gmail sends a tailored message per risk branch (no email for "none")

7\. \*\*Log the action\*\* — every intervention is appended to a `RiskLog` sheet for record-keeping



\---



🛠️ Tech Stack



| Tool | Purpose |

|---|---|

| 🔧 n8n | Workflow automation/orchestration |

| 📊 Google Sheets | Data source + logging |

| ✨ Google Gemini API | AI classification \& message generation |

| 📧 Gmail | Automated email delivery |



\---



🖼️ Screenshots



Full Workflow Canvas

!\[Workflow Canvas](screenshots/canvas.png)



AI Classification Output

!\[AI Output](screenshots/ai-output.png)



Automated Emails Sent

!\[Sent Emails](screenshots/sent-emails.png)



RiskLog Sheet

!\[Risk Log](screenshots/risklog.png)



\---



📂 Workflow File



The full exported n8n workflow is available at \[`workflow/TrackMate.json`](workflow/TrackMate.json). Import it into your own n8n instance and connect your own Google Sheets, Gemini, and Gmail credentials to run it.



\---



🚀 Future Improvements



\- Switch from Manual Trigger to a Schedule Trigger for fully automated runs

\- Add request batching/throttling to handle Gemini API rate limits at scale

\- Build a simple dashboard for mentors to review flagged students and outreach history

\- Log "no action needed" entries for the `none` branch for full audit coverage



\---



👩‍💻 Built by Anushree Bonde

