# Monthly Account Review

## What This Is

A comprehensive account intelligence prompt built for Senior Solution Engineers supporting healthcare accounts. It acts as your personal Account Analyst, pulling from every enterprise data source available in Microsoft 365 to generate a full monthly review across all your accounts, automatically delivered on the first business day of every month.

Each run produces four outputs: a structured Monthly Account Review Report, a one-page Executive Summary, an Executive PowerPoint, and an HTML presentation, all emailed directly to you.

> This prompt is scoped to M365 Copilot and Copilot Chat activity across a defined list. Swap in your own accounts and adjust the data sources to match your territory and role.

---

## Prompt

Act as my Account Analyst.
Research the `Insert projects, accounts, etc` listed by below that I support as a `{Role}`.
Use enterprise sources:

Outlook emails
Teams chats and channels
Calendar and meetings
OneDrive and SharePoint files
Dynamics / CRM
ServiceNow
Azure DevOps
Meeting transcripts and notes
Focus specifically on: M365 Copilot and Copilot Chat related work.


PRIMARY OUTPUT: Monthly Account Review Report `Adjust based on your prefernces and persona, below are examples to use`
Deliver a single comprehensive structured report with the following sections:

Activities & Scope List the concrete activities completed in the last 6–12 months:

Workshops
Executive briefings
Enablement sessions
Pilots
Deployments
Governance work
Agent building
Training
Follow‑ups
Include: Date Audience Artifacts produced Linked materials

Opportunities & Projects Enumerate each opportunity or project tied to M365 Copilot and Copilot Chat.
For each include: Opportunity name or ID
Stage
Products involved
Deal size if available
Timeline or milestones
Next steps

Revenue Impact For each opportunity or project provide:
ACV or TCV if stated
License counts
SKU types
Pilot to paid conversions
Expansion potential
If exact revenue is missing, provide best available proxy:
Quoted license quantities
PO mentions
Budget approvals
Forecast notes
Relevant CRM fields

Key Stakeholders List stakeholders engaged:
Name
Title
Function
Org
Role in decision: Economic buyer
Technical evaluator
Champion
Blocker
Include links to: Meeting invites
Email threads
Chats

Successes (with evidence) Summarize measurable outcomes:
Adoption metrics
Paid MAU
Training attendance
Pilot results
Time savings
Satisfaction scores
Governance milestones
Agent launches
Cite: Sources
Dates
Relevant executive or team quotes when present

Blockers (with detail) Identify blockers and risks:
Security or compliance concerns
Licensing constraints
Technical dependencies
Tenant configuration issues
Data access limitations
Procurement delays
Competing priorities
Include: Owner
Impact
Recommended mitigation

Action Plan Recommend 3–5 concrete next actions to advance:
Revenue
Adoption
Executive alignment
Blocker removal
Align actions to stakeholder roles where possible.


FORMATTING
Use: Clear headings
Bulleted lists
Short paragraphs
Link to: Emails
Chats
Files
Meetings
Transcripts
Include: Timeline of major activities and decisions
Call out numbers prominently
Prioritize: Last 12 months of activity
Upcoming meetings or opportunities in the next quarter


SECONDARY OUTPUTS
After generating the Monthly Account Review Report:

Generate an Executive Summary Summarize: Account momentum
Revenue signals
Major risks
Expansion opportunities
Required leadership actions
Limit to one page equivalent.

Generate an Executive PowerPoint Presentation
Include slides for: Account Overview
Copilot Activities Completed
Active Opportunities
Revenue Signals
Stakeholder Map
Success Outcomes
Blockers and Risk
Recommended Next Actions
Executive Decision Points
Use concise executive language suitable for leadership review.

Generate an HTML Presentation
Create an HTML based presentation that: Summarizes the report visually
Highlights trends, blockers, and opportunities
Allows async review


DELIVERY
Send an email to me with:
Subject: Monthly Account Review
Body: Include the Executive Summary inline
Attachments: Full Monthly Account Review Report
Executive PowerPoint Presentation
HTML Presentation


SCHEDULE
Run this task automatically on the first business day of each month on a recurring basis.


ACCOUNT LIST `Optional - callout your customers, projects, etc here`
