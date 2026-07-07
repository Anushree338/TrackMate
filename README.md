\# TrackMate



TrackMate is an AI-powered academic risk detection and intervention workflow built with n8n. It automatically identifies students showing signs of academic decline and sends personalized, empathetic outreach emails — helping educators intervene early.



\## Problem



Students often show early warning signs of academic struggle — a sudden score drop, chronic low performance, or a slow decline — but these patterns can go unnoticed until it's too late. Manually reviewing every student's data isn't scalable.



\## Solution



TrackMate reads student performance data from Google Sheets, uses Google's Gemini AI to classify each student's risk pattern, and automatically sends a tailored, supportive email based on the type of risk detected — then logs the action for tracking.



\## How it works



1\. \*\*Trigger\*\* — Workflow starts (manual trigger for demo; can be swapped for a scheduled trigger in production).

2\. \*\*Read data\*\* — Pulls student records (attendance, quiz scores, past averages, assignment status) from a Google Sheet.

3\. \*\*AI classification\*\* — Each student's data is sent to Gemini, which classifies them into one of four categories:

&#x20;  - `sudden` — a sharp, recent score drop

&#x20;  - `chronic` — consistently low performance

&#x20;  - `gradual` — slow, ongoing decline

&#x20;  - `none` — no concerning pattern

4\. \*\*Parse response\*\* — A Code node extracts the AI's JSON output (risk type, reasoning, and a ready-to-send empathetic message).

5\. \*\*Route by risk type\*\* — A Switch node branches the workflow based on the classification.

6\. \*\*Send email\*\* — Gmail node sends a tailored message to the student for each risk branch (no email sent for "none").

7\. \*\*Log the action\*\* — Each intervention is appended to a `RiskLog` sheet for record-keeping (student, risk type, reason, action taken, date).



\## Tech stack



\- \*\*n8n\*\* — workflow automation/orchestration

\- \*\*Google Sheets\*\* — data source and logging

\- \*\*Google Gemini API\*\* — AI classification and message generation

\- \*\*Gmail\*\* — automated email delivery



\## Screenshots



| Description | Screenshot |

|---|---|

| Full workflow canvas | `screenshots/canvas.png` |

| AI classification output (JSON) | `screenshots/ai-output.png` |

| Sent emails | `screenshots/sent-emails.png` |

| RiskLog sheet entries | `screenshots/risklog.png` |



\## Workflow file



The full exported n8n workflow is available at \[`workflow/TrackMate.json`](workflow/TrackMate.json). Import it into your own n8n instance and connect your own Google Sheets, Gemini, and Gmail credentials to run it.



\## Future improvements



\- Switch from Manual Trigger to a Schedule Trigger for fully automated daily/weekly runs.

\- Add request batching/throttling to handle Gemini API rate limits at scale.

\- Build a simple dashboard for mentors to review flagged students and outreach history.

\- Expand the "none" branch to optionally log a "no action needed" entry for full audit coverage.

