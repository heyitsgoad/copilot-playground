# IT Power Moves Prompt Pack

## What This Is

This is the set of prompts I hand to IT teams when I want Copilot to actually earn its seat in a technical room. They are small, copy-paste lines that take you from a cryptic error log or a blank PowerShell window to a clear next step. They cover the technical work you do in Copilot Chat plus the everyday wins in Excel, Word, and Outlook. Two habits run through all of them: explain before you run, and first draft then you verify. The human stays the approver, which matters a lot when you work in change control.

> [!TIP]
> Swap anything in `[brackets]` for your own details, like `[paste]` for your log or script, or your own asset tag format. The more specific you are, the sharper the result.

> [!IMPORTANT]
> These are first drafts and explanations, not blind automation. Always read and verify any script, command, or config change before you run it in production.

---

## Copilot Chat: The Technical Room

The golden nuggets for the console. Paste a log, a script, or a config and let Copilot decode, explain, or draft.

- "Paste this error/log. What is it, the likely cause, and my next steps? [paste]"
- "Explain what this PowerShell does and what it changes before I run it. [paste]"
- "Write a PowerShell one-liner to find AD users who haven't logged in for 90 days."
- "Give me a regex for our asset tag format `[AB-1234-CD]` and explain each part."
- "Read this stack trace, tell me the failing component, the likely root cause, and the three most probable fixes ranked by effort. [paste]"
- "Diff these two config files and explain only the differences that would change runtime behavior. [paste A] [paste B]"
- "Convert this Bash script to PowerShell, keep the logic identical, and flag anything that won't map cleanly. [paste]"
- "Write a query to find sign-ins from impossible-travel locations in the last 24 hours, and explain each clause."
- "Explain what this registry change does, the risk, and how to roll it back. [paste]"
- "Here's the command I'm about to run in production. What could go wrong, and how do I make it safer? [paste]"

---

## Document As You Go

The work nobody wants to do by hand. Turn rough notes and incidents into clean, audit-ready docs.

- "Turn these rough troubleshooting notes into a clean runbook with prerequisites, steps, and a rollback plan. [paste]"
- "Draft a change-control summary for this fix: what's changing, blast radius, backout plan, and validation steps. [paste]"
- "From this incident timeline, draft a root-cause analysis with contributing factors and follow-up actions. [paste]"

---

## Excel

For inventory, license tracking, and log work. Best shown in-app so people see Copilot act on their real file.

- "Explain what this formula does step by step and tell me where it could break. [paste]"
- "I have asset tags in column A and last-logon dates in column B. Write a formula to flag any device not seen in 90+ days."
- "Suggest a PivotTable to summarize this license inventory by department and license type, and tell me exactly which fields go where."
- "This export has inconsistent date formats and trailing spaces. Give me steps to standardize it without breaking the asset IDs."
- "Analyze this CPU and memory usage table and highlight the top anomalies worth investigating."
- "Tell me how to color any row red where Status is Expired and the renewal date is within 30 days."
- "Extract the hostname out of these full FQDN entries in column A into column B."

---

## Word

For policies, SOPs, and audit-ready docs.

- "Turn these bullet points into a formatted standard operating procedure with numbered steps and a prerequisites section. [paste]"
- "Summarize this security policy into a one-page quick reference for the help desk. [paste]"
- "Rewrite this technical change notice so a non-technical department can understand the impact and timing. [paste]"
- "Review this incident response plan and list what's missing compared to a standard IR framework. [paste]"
- "Create a reusable change-request template with sections for scope, risk, backout, approvals, and validation."
- "Cut this runbook down by 30% without losing any required step. [paste]"

---

## Outlook

For the on-call inbox and stakeholder comms.

- "Summarize this email thread, list every decision made, and who owns each open action item. [paste/thread]"
- "Draft a clear, calm outage notification for end users: what's affected, what we're doing, and the next update time."
- "Summarize everything from `[vendor or person]` this week and flag anything that needs a reply today."
- "Draft a reply to this vendor proposing three maintenance windows next week, all after 8pm. [paste]"
- "Pull every action item assigned to me out of my unread mail from the last two days."
- "Rewrite this escalation so it's direct about the SLA breach but still professional. [paste]"
- "Find the recent emails and files related to my next meeting and give me a one-paragraph brief."

---

## Two Habits to Teach Alongside These

- **Explain before you run.** Have Copilot tell you what a script or command touches before it executes. This keeps you in control and turns every prompt into a learning moment.
- **First draft, then you verify.** Copilot writes the regex, the one-liner, or the runbook. You confirm it does what you expect. That split is the whole point, especially in regulated or change-controlled environments.
