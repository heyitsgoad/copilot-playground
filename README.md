This repository is a portfolio of my Copilot agents, prompt library, and videos that show how I design, ship, and teach AI solutions across Microsoft 365, Copilot Studio, and Agent 365.

Audience: customers, partners, and hiring managers who want to see real work, not slides
Focus: measurable outcomes, secure enterprise patterns, and hands‑on examples
Tech: Microsoft 365 Copilot, Copilot Chat, Copilot Studio, Agent 365, Purview, Power Platform, and ChatGPT

AI Agents
Production‑ready and workshop‑ready agents. Each folder includes a README, governance notes, and a minimal test script.
Categories

Healthcare

Care‑Ops Triage Agent: routes non‑clinical requests, respects labels and DLP
Meeting Intelligence Agent: action items from clinical and ops calls, writes to Teams/Planner


Productivity (M365)

Inbox Prioritizer: flags high‑signal emails, drafts replies with org‑safe grounding
Doc Review Assistant: suggests edits, tracks changes, logs activity for audit


Data‑Ops

Content Signals Agent: SAM + SharePoint access reviews to reduce oversharing
Labeling Coach: recommends sensitivity labels based on usage patterns



Each Agent Includes

Overview: problem, outcome, measurable metric
Architecture: boundaries, data flow, controls (Purview/DLP/SAM)
Setup: environment, connectors, variables, permissions
Run: quick start script or solution
Governance: what’s logged, who can execute, cost guardrails


Category-first organization takes cues from curated LLM agent lists. [github.com]


Prompt Library
Actionable prompts organized by app and role. Short, tested, and written to work with default enterprise controls.
Organization

M365 Apps: Outlook, Teams, Word, Excel, PowerPoint
Studio: building, testing, connector policies, evaluation
Governance: DLP, labels, insider risk, eDiscovery language

File Pattern

Use case: one line
Prompt: copy‑paste block
Optional inputs: variables, data sources
Output target: reply email, doc comment, task list
Notes: risks, label hints, audit logging


Copilot Management & Governance
This section is built for IT admins and security teams. It features short videos and runnable guides that show how to manage, govern, and observe Copilot and agents at scale.
Video Tracks

Admin Center: Copilot Control System

Access and billing controls
Frontier and in‑app feature routing
Scoped rollouts by user or group


Copilot Studio + Power Platform Governance

Managed Environments, environment routing
Connector risk controls and DLP policies
Cost management and execution limits


Purview for M365 + Agents

Sensitivity labels, policy hints, DLP rules
Insider risk, audit/eDiscovery baselines
How labeling shapes Copilot visibility


SharePoint Advanced Management (SAM)

Oversharing baselines, lifecycle cleanup
Access reviews, RAC/RCD
Content signals so Copilot “sees” the right data



Each video folder includes:

Context: what you’ll change and why
Steps: numbered actions, screenshots or CLI snippets
Checks: how to verify policy impact
Roll‑back: how to safely revert
