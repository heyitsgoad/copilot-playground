# IT Power Moves Prompt Pack

## What This Is

This is the set of prompts I hand to IT teams when I want Copilot to actually earn its seat in a technical room. They are small, copy-paste lines that take you from a cryptic error log or a blank PowerShell window to a clear next step.

They cover the technical work you do in Copilot Chat plus the everyday wins in Excel, Word, and Outlook. Two habits run through all of them: explain before you run, and first draft then you verify. The human stays the approver, which matters a lot when you work in change control.

> [!TIP]
> Swap anything in `[brackets]` for your own details, like `[paste]` for your log or script, or your own asset tag format. The more specific you are, the sharper the result.

> [!IMPORTANT]
> These are first drafts and explanations, not blind automation. Always read and verify any script, command, or config change before you run it in production.

---

## Copilot Chat: The Technical Room

The golden nuggets for the console. Paste a log, a script, or a config and let Copilot decode, explain, or draft.

### Error log triage

```
Paste this error/log. What is it, the likely cause, and my next steps? [paste]
```

### PowerShell safety check

```
Explain what this PowerShell does and what it changes before I run it. [paste]
```

### Inactive AD users

```
Write a PowerShell one-liner to find AD users who haven't logged in for 90 days.
```

### Asset tag regex

```
Give me a regex for our asset tag format `[AB-1234-CD]` and explain each part.
```

### Stack trace analysis

```
Read this stack trace, tell me the failing component, the likely root cause, and the three most probable fixes ranked by effort. [paste]
```

### Runtime config diff

```
Diff these two config files and explain only the differences that would change runtime behavior. [paste A] [paste B]
```

### Bash to PowerShell

```
Convert this Bash script to PowerShell, keep the logic identical, and flag anything that won't map cleanly. [paste]
```

### Impossible travel query

```
Write a query to find sign-ins from impossible-travel locations in the last 24 hours, and explain each clause.
```

### Registry change review

```
Explain what this registry change does, the risk, and how to roll it back. [paste]
```

### Production command review

```
Here's the command I'm about to run in production. What could go wrong, and how do I make it safer? [paste]
```

---

## Document As You Go

The work nobody wants to do by hand. Turn rough notes and incidents into clean, audit-ready docs.

### Troubleshooting runbook

```
Turn these rough troubleshooting notes into a clean runbook with prerequisites, steps, and a rollback plan. [paste]
```

### Change-control summary

```
Draft a change-control summary for this fix: what's changing, blast radius, backout plan, and validation steps. [paste]
```

### Root-cause analysis

```
From this incident timeline, draft a root-cause analysis with contributing factors and follow-up actions. [paste]
```

---

## Excel

For inventory, license tracking, and log work. Best shown in-app so people see Copilot act on their real file.

### Formula explanation

```
Explain what this formula does step by step and tell me where it could break. [paste]
```

### Dormant device formula

```
I have asset tags in column A and last-logon dates in column B. Write a formula to flag any device not seen in 90+ days.
```

### License PivotTable

```
Suggest a PivotTable to summarize this license inventory by department and license type, and tell me exactly which fields go where.
```

### Clean export data

```
This export has inconsistent date formats and trailing spaces. Give me steps to standardize it without breaking the asset IDs.
```

### Resource anomaly analysis

```
Analyze this CPU and memory usage table and highlight the top anomalies worth investigating.
```

### Expired row formatting

```
Tell me how to color any row red where Status is Expired and the renewal date is within 30 days.
```

### Hostname extraction

```
Extract the hostname out of these full FQDN entries in column A into column B.
```

---

## Word

For policies, SOPs, and audit-ready docs.

### SOP from bullets

```
Turn these bullet points into a formatted standard operating procedure with numbered steps and a prerequisites section. [paste]
```

### Security policy quick reference

```
Summarize this security policy into a one-page quick reference for the help desk. [paste]
```

### Plain-language change notice

```
Rewrite this technical change notice so a non-technical department can understand the impact and timing. [paste]
```

### Incident response review

```
Review this incident response plan and list what's missing compared to a standard IR framework. [paste]
```

### Change-request template

```
Create a reusable change-request template with sections for scope, risk, backout, approvals, and validation.
```

### Runbook trim

```
Cut this runbook down by 30% without losing any required step. [paste]
```

---

## Outlook

For the on-call inbox and stakeholder comms.

### Thread summary

```
Summarize this email thread, list every decision made, and who owns each open action item. [paste/thread]
```

### Outage notification

```
Draft a clear, calm outage notification for end users: what's affected, what we're doing, and the next update time.
```

### Weekly sender summary

```
Summarize everything from `[vendor or person]` this week and flag anything that needs a reply today.
```

### Maintenance window reply

```
Draft a reply to this vendor proposing three maintenance windows next week, all after 8pm. [paste]
```

### Unread mail actions

```
Pull every action item assigned to me out of my unread mail from the last two days.
```

### SLA escalation rewrite

```
Rewrite this escalation so it's direct about the SLA breach but still professional. [paste]
```

### Next meeting brief

```
Find the recent emails and files related to my next meeting and give me a one-paragraph brief.
```

---

## Two Habits to Teach Alongside These

- **Explain before you run.** Have Copilot tell you what a script or command touches before it executes. This keeps you in control and turns every prompt into a learning moment.
- **First draft, then you verify.** Copilot writes the regex, the one-liner, or the runbook. You confirm it does what you expect. That split is the whole point, especially in regulated or change-controlled environments.

---

[Back to the Prompt Playground](../README.md#prompt-playground)
