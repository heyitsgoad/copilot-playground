# Monthly Account Review

## What This Is

A comprehensive account intelligence prompt that acts as your personal Account Analyst. It pulls from every enterprise data source available in Microsoft 365 to generate a full monthly review across your accounts, automatically delivered on the first business day of every month.

Each run produces four outputs: a structured Monthly Account Review Report, a one-page Executive Summary, an Executive PowerPoint, and an HTML presentation, all emailed directly to you.

> [!TIP]
> Swap in your own accounts, role, and data sources before running. The structure below is a template — adjust the TPID list, persona, and output preferences to match your territory and engagement model.

---

## Prompt

Act as my Account Analyst.
Research the `Insert projects, accounts, etc` listed below that I support as a `Role`.

---

### Data Sources

Use the following enterprise sources:

- Outlook emails
- Teams chats and channels
- Calendar and meetings
- OneDrive and SharePoint files
- Dynamics / CRM
- ServiceNow
- Azure DevOps
- Meeting transcripts and notes

Focus specifically on M365 Copilot and Copilot Chat related work.

---

## Primary Output: Monthly Account Review Report

> [!NOTE]
> Adjust section focus based on your preferences and persona. The examples below are starting points.

Deliver a single comprehensive structured report with the following sections:

---

### Section 1: Activities & Scope

List the concrete activities completed in the last 6–12 months:

- Workshops
- Executive briefings
- Enablement sessions
- Pilots
- Deployments
- Governance work
- Agent building
- Training
- Follow-ups

Include for each: Date, Audience, Artifacts produced, and Linked materials.

---

### Section 2: Opportunities & Projects

Enumerate each opportunity or project tied to M365 Copilot and Copilot Chat.

Include for each:

| Field | Details |
|---|---|
| Opportunity name or ID | |
| Stage | |
| Products involved | |
| Deal size if available | |
| Timeline or milestones | |
| Next steps | |

---

### Section 3: Revenue Impact

For each opportunity or project provide:

- ACV or TCV if stated
- License counts
- SKU types
- Pilot to paid conversions
- Expansion potential

If exact revenue is missing, provide the best available proxy:

- Quoted license quantities
- PO mentions
- Budget approvals
- Forecast notes
- Relevant CRM fields

---

### Section 4: Key Stakeholders

List stakeholders engaged:

| Name | Title | Function | Org | Role in Decision |
|---|---|---|---|---|

Role in decision options: Economic Buyer, Technical Evaluator, Champion, Blocker

Include links to meeting invites, email threads, and chats where available.

---

### Section 5: Successes (with Evidence)

Summarize measurable outcomes:

- Adoption metrics
- Paid MAU
- Training attendance
- Pilot results
- Time savings
- Satisfaction scores
- Governance milestones
- Agent launches

Cite sources, dates, and relevant executive or team quotes when present.

---

### Section 6: Blockers (with Detail)

Identify blockers and risks:

- Security or compliance concerns
- Licensing constraints
- Technical dependencies
- Tenant configuration issues
- Data access limitations
- Procurement delays
- Competing priorities

Include for each: Owner, Impact, and Recommended mitigation.

---

### Section 7: Action Plan

Recommend 3–5 concrete next actions to advance:

- Revenue
- Adoption
- Executive alignment
- Blocker removal

Align actions to stakeholder roles where possible.

---

### Formatting Guidelines

- Use clear headings and bulleted lists
- Link to emails, chats, files, meetings, and transcripts where available
- Include a timeline of major activities and decisions
- Call out numbers prominently
- Prioritize the last 12 months of activity and upcoming opportunities in the next quarter

---

## Secondary Outputs

---

### A. Executive Summary

Summarize:

- Account momentum
- Revenue signals
- Major risks
- Expansion opportunities
- Required leadership actions

Limit to one page equivalent.

---

### B. Executive PowerPoint Presentation

Include slides for:

- Account Overview
- Copilot Activities Completed
- Active Opportunities
- Revenue Signals
- Stakeholder Map
- Success Outcomes
- Blockers and Risk
- Recommended Next Actions
- Executive Decision Points

Use concise executive language suitable for leadership review.

---

### C. HTML Presentation

Create an HTML-based presentation that:

- Summarizes the report visually
- Highlights trends, blockers, and opportunities
- Allows async review

---

## Delivery

Send an email with:

- **Subject:** `Monthly Account Review`
- **Body:** Executive Summary inline
- **Attachments:** Full Monthly Account Review Report, Executive PowerPoint, HTML Presentation

---

## Schedule

Run this task automatically on the first business day of each month on a recurring basis.
