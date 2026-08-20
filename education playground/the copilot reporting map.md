# The Copilot Reporting Map

Every report you can use to measure, govern, and prove out Microsoft 365 Copilot, in one place.

You get asked "how is Copilot actually going?" and the answer lives in nine different portals. Adoption numbers are in one place, credit burn in another, oversharing risk in a third, and the audit trail somewhere else entirely. Nobody hands you a map.

This is the map. All 36 reports below are real, documented, customer-side reports you can open in your own tenant today. No internal Microsoft tools, no seller dashboards. Each row tells you where it lives, what it shows, and what license or role you need to see it.

**Prefer to filter and search instead of scroll?** [Open the interactive version](https://heyitsgoad.github.io/copilot-playground/education%20playground/assets/the%20copilot%20reporting%20map/), which lets you filter all 36 by portal, GA vs Preview, and topic.

**Checked against Microsoft Learn as of August 20, 2026.** This space moves fast, so GA and Preview status is called out on every row that has one.

> [!NOTE]
> This is a personal community resource. The analysis and opinions are my own and are not an official Microsoft position. Always confirm licensing against your own agreement.

---

## Start here

Pick the question you're actually being asked.

| The question | The report | Portal |
| --- | --- | --- |
| Are people using Copilot? | [Microsoft 365 Copilot Usage](#1-microsoft-365-copilot-usage-report) | M365 admin center |
| Who should get the next 500 licenses? | [Copilot Readiness](#2-copilot-readiness-report) | M365 admin center |
| Is it saving anyone time? | [Copilot Dashboard, Impact](#13-microsoft-copilot-dashboard) | Viva Insights |
| What are the unlicensed people doing? | [Copilot Chat Usage](#3-microsoft-copilot-chat-usage-report) | M365 admin center |
| What agents exist in my tenant? | [Agent Registry](#19-agent-registry) | M365 admin center |
| Who is burning credits? | [Copilot Credits](#7-microsoft-copilot-credits-report) and [Consumption Dashboard](#15-consumption-dashboard) | Admin center, Viva |
| Will Copilot surface something it shouldn't? | [Data Access Governance](#26-data-access-governance-dag-reports) | SharePoint admin center |
| What did Copilot touch when it answered that? | [Purview Audit](#30-purview-audit-for-copilot) | Purview |
| Is anyone pasting secrets into ChatGPT? | [DSPM for AI](#29-dspm-for-ai) | Purview |
| Legal needs the prompts from a specific user | [eDiscovery](#31-ediscovery-for-copilot-interactions) | Purview |

---

## Section 1: Microsoft 365 admin center, the Copilot reports

These are your daily drivers. All of them live under **Reports > Usage**, except Cowork, which sits under the **Copilot** node in the left nav.

Direct link to the usage reports hub: [admin.microsoft.com/Adminportal/Home#/reportsUsage](https://admin.microsoft.com/Adminportal/Home#/reportsUsage)

### 1. Microsoft 365 Copilot Usage report

| | |
| --- | --- |
| **Where** | Reports > Usage > Microsoft Copilot > Copilot > **Usage** tab |
| **What it shows** | Enabled vs. active users and active user rate. Total prompts submitted and average per user. Per-app adoption across Teams, Outlook, Word, Excel, PowerPoint, OneNote, Loop, Edge, Copilot Chat (work), and Copilot Chat (web). Per-user table with prompts submitted, active days, and a fixed last-activity date per app. |
| **History** | 7 / 28 / 90 / 180 days. The per-user table always covers 180 days no matter which filter you pick. |
| **Latency** | Within 48 hours of end of day UTC |
| **Clouds** | Public, GCC, GCC-High, DoD |
| **Status** | GA |
| **Docs** | [Microsoft 365 Copilot usage](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/microsoft-365-copilot-usage) |

This is the report leadership means when they ask for "the Copilot numbers." Two things to know before you present it.

**"Active" means an intentional action.** Opening the Copilot pane or clicking the ribbon icon doesn't count. Submitting a prompt does. When your number looks lower than the buzz in the hallway, this is usually why.

**Users stay in the table for 180 days after you pull their license.** Handy for churn analysis, misleading if you read the raw row count as your license position.

### 2. Copilot Readiness report

| | |
| --- | --- |
| **Where** | Reports > Usage > Microsoft Copilot > Copilot > **Readiness** tab |
| **What it shows** | Prerequisite licenses, users on an eligible update channel (Current or Monthly Enterprise), assigned licenses, and available licenses. Ranks unlicensed users by M365 activity and flags the top 25% as suggested Copilot candidates. Per-user table covering Teams meetings, Teams chat, Outlook email, and Office doc collaboration. |
| **History** | Past 28 days. CSV export covers 30 days of engagement. |
| **Latency** | Within 72 hours |
| **Clouds** | Public only |
| **Status** | GA |
| **Docs** | [Microsoft 365 Copilot readiness](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/microsoft-365-copilot-readiness) |

The most underused report in the admin center. Export the CSV and you have a defensible answer to "who gets the next wave," backed by actual collaboration behavior instead of org chart politics.

### 3. Microsoft Copilot Chat Usage report

| | |
| --- | --- |
| **Where** | Reports > Usage > Microsoft Copilot > **Copilot Chat** |
| **What it shows** | Active users, average daily active users, total prompts, and average prompts per user for people **without** a paid Copilot license. Adoption split across Edge, the Copilot app, Teams, Outlook, m365.cloud.microsoft/chat, Word, Excel, PowerPoint, and OneNote. |
| **History** | 7 / 28 / 90 / 180 days |
| **Latency** | Within 48 hours |
| **Clouds** | Public, GCC, GCC-High, DoD |
| **Status** | GA |
| **Docs** | [Microsoft Copilot usage](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/microsoft-copilot-usage) |

Separate report from #1, and people miss this constantly. #1 covers licensed users. This one covers everyone else. You need both to answer "how many people in this company touch Copilot." It's also your best upsell signal, since heavy Chat users with no license are the easiest business case you'll ever build.

### 4. Microsoft Copilot Agents Usage report

| | |
| --- | --- |
| **Where** | Reports > Usage > Microsoft Copilot > **Agents** |
| **What it shows** | Total active users split into licensed and unlicensed, total active agents, a per-agent table with active users and surface, and a licensed vs. unlicensed trend chart. Covers Microsoft-built, third-party, and org-built agents across declarative, SharePoint, and custom engine types. |
| **History** | 7 or 30 days |
| **Latency** | Within 1 hour |
| **Clouds** | Public only |
| **Status** | **Preview** |
| **Docs** | [Microsoft 365 Copilot agents usage](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/microsoft-365-copilot-agents-new) |

This replaced an older agents report that only counted agents your own org built and ran on a 72-hour delay. If you bookmarked the old one, [it's deprecated](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/microsoft-365-copilot-agents). Move to this one.

### 5. Microsoft 365 Copilot Connectors Usage report

| | |
| --- | --- |
| **Where** | Reports > Usage > Microsoft Copilot > **Connectors** |
| **What it shows** | Connections used by Copilot, connections used by agents, active connector users, and total connector-grounded responses. Broken out per connector and per user. |
| **History** | 7 or 30 days |
| **Latency** | Within 1 hour |
| **Clouds** | Public only |
| **Status** | **Preview** |
| **Docs** | [Copilot connectors usage](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/microsoft-365-copilot-connectors-usage) |

A connection only counts when a licensed user gets a response that actually cites connector content. If you spent six months standing up a ServiceNow connector, this is the report that tells you whether it earned its keep. Cowork connector usage isn't covered yet.

### 6. Microsoft Copilot Search Usage report

| | |
| --- | --- |
| **Where** | Reports > Usage > Microsoft Copilot > **Copilot Search** |
| **What it shows** | Active users, average daily active users, total searches, and average searches per user, plus a per-user table. |
| **History** | 7 / 30 / 90 / 180 days |
| **Latency** | Within 1 hour |
| **Clouds** | Public only |
| **Status** | **Preview** |
| **Docs** | [Copilot search usage](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/microsoft-365-copilot-search-usage) |

### 7. Microsoft Copilot Credits report

| | |
| --- | --- |
| **Where** | Reports > Usage > Microsoft Copilot > **Credits** |
| **What it shows** | Credits consumed by unlicensed users hitting metered agents in Copilot Chat. Cumulative and daily views, broken down by user, by agent, by billing policy, and by agent-user pair. Fires an alert when a user crosses roughly 2,000 to 3,000 credits in 30 days. |
| **History** | 7 or 30 days during preview. Nothing before May 3, 2025. |
| **Latency** | Within 1 hour |
| **Clouds** | Public only |
| **Status** | **Preview** |
| **Docs** | [Microsoft Copilot credits](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/microsoft-365-copilot-credits) |

Your early warning system for pay-as-you-go surprises. A single complex prompt against a graph-grounded agent runs about 12 credits, so a handful of enthusiastic users move the invoice faster than most finance teams expect.

### 8. Cowork Usage report

| | |
| --- | --- |
| **Where** | Admin center > **Copilot** (left nav) > **Cowork**. Not under Reports > Usage. |
| **What it shows** | Active Cowork users, total Cowork tasks, average tasks per user, and retained users measured across two consecutive 7-day windows. Daily active user trend and a user-initiated vs. scheduled task split. Per-user table with total, scheduled, and user-initiated task counts. Also shows your billing grace period countdown. |
| **History** | Data available from April 1, 2026 |
| **Clouds** | Public only |
| **Status** | GA |
| **Docs** | [Cowork usage report](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/cowork-usage-report) |

Yes, Cowork reporting exists now, and it's GA. The grace period counter matters: it tells you how long before Cowork access can be suspended if you haven't set up consumptive billing. Watch the retained users metric more than raw active users, since scheduled tasks make one-time curiosity look like adoption.

---

## Section 2: The workload reports that tell you if the ground is ready

Copilot rides on Teams, Outlook, SharePoint, and OneDrive. When Copilot adoption stalls, the cause is often that people weren't collaborating in those tools to begin with. Same nav: **Reports > Usage**.

| Report | What it shows |
| --- | --- |
| **Active Users** | Which services each person actually uses. Your baseline denominator. |
| **Microsoft 365 Apps Usage** | Desktop, web, and mobile app usage by platform. Cross-check against update channel. |
| **Teams User Activity** | Meetings, chats, calls, channel messages per user. Predicts Copilot in Teams uptake better than anything else. |
| **Teams Device Usage / Team Activity** | Platform mix and per-team activity. |
| **Email Activity / Email Apps Usage / Mailbox Usage** | Send and read volume, client mix, mailbox size. |
| **SharePoint Site Usage / Activity / Storage** | Files viewed, edited, shared, and where content lives. |
| **OneDrive User Activity / Usage** | Per-user file activity and storage. |
| **Microsoft 365 Groups** | Group activity and storage. |
| **Viva Engage Activity / Device / Groups** | Community engagement. |
| **Viva Learning, Viva Insights, Viva Goals Activity** | Viva app engagement. |
| **Forms, Project, Visio, Office Activations, Browser Usage** | Long tail. Browser Usage is useful for Copilot in Edge readiness. |

All of these run on the same role list and support 7, 30, 90, and 180-day windows. Full list: [usage reports overview](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports).

### 9. Adoption Score

| | |
| --- | --- |
| **Where** | Reports > **Adoption Score** |
| **What it shows** | People experiences scoring across communication, meetings, content collaboration, teamwork, and mobility, plus technology experiences via Endpoint Analytics. Now carries an AI adoption category. |
| **Docs** | [Adoption Score](https://learn.microsoft.com/en-us/microsoft-365/admin/adoption/adoption-score) |

### 10. Message center, Service health, and the roadmap

Not usage reports, but the reason your numbers moved.

| Surface | Use it for |
| --- | --- |
| **Message center** (admin center > Health > Message center) | Copilot feature changes landing in your tenant. Filter to Copilot and set up the weekly digest. |
| **Service health** (admin center > Health > Service health) | Whether a metric dropped because of an incident. Copilot Dashboard had a real data accuracy issue from June 2025 to February 2026. |
| **[Microsoft 365 Roadmap](https://www.microsoft.com/microsoft-365/roadmap)** | What reporting is coming next. |

### 11. Copilot license and seat position

| | |
| --- | --- |
| **Where** | Billing > **Licenses**, Billing > **Your products**, Users > **Active users** |
| **What it shows** | Purchased vs. assigned vs. available seats per SKU, and per-user license detail. |

For "which humans have a license and aren't using it," pair this with the Readiness report rather than reading Billing alone.

### 12. Microsoft 365 Apps admin center

| | |
| --- | --- |
| **Where** | [config.office.com](https://config.office.com) |
| **What it shows** | Update channel distribution, app inventory, servicing health, and add-in readiness. |

Copilot requires Current Channel or Monthly Enterprise Channel. When a user swears Copilot isn't showing up in Word, check here first.

---

## Section 3: Copilot Analytics, the adoption and impact layer

Everything in this section lives in the **Viva Insights web app** at [analysis.insights.cloud.microsoft](https://analysis.insights.cloud.microsoft), not the admin center.

Microsoft has been shifting this toward the "Microsoft 365 Copilot Analytics" name in the UI, while Learn docs still say Viva Insights. Treat them as the same thing.

**The 50-license cliff matters more than anything else here.** Under 50 Copilot licenses you get Readiness, Adoption, and Impact. At 50 or more Copilot licenses, or 50 or more Viva Insights licenses, you also get the Agent Dashboard, benchmarks, sentiment integration, week and month trendlines, manager group views, and intelligent summaries. If you're piloting with 40 seats, you are deliberately buying a worse dashboard.

### 13. Microsoft Copilot Dashboard

| | |
| --- | --- |
| **Where** | Viva Insights web app > **Copilot Dashboard** |
| **What it shows** | Four sections. **Readiness**: licenses assigned, eligible update channels, actionable unblock cards. **Adoption**: active users on a 28-day window, returning users, per-app and per-feature breakdown, and user segments split into power, habitual, and novice. **Impact**: Copilot actions taken, Copilot assisted hours, assisted value, and satisfaction rate. **Sentiment**: survey results from Glint, Pulse, or an uploaded CSV. |
| **Who sees it** | Senior leaders automatically in tenants above 2,500 users, Global Admins, Viva Insights analysts with global partition access, and managers only if an admin enables them. IT and adoption leads must be added manually. |
| **Data** | Rolling 28 days, up to 6 days behind, 6 months of trend history. New licenses take up to 7 days to appear. |
| **Status** | GA |
| **Docs** | [Microsoft Copilot Dashboard](https://learn.microsoft.com/en-us/viva/insights/org-team-insights/copilot-dashboard) |

**Know how assisted hours are calculated before you put them in a board deck.** The formula counts meeting hours summarized, plus 6 minutes per search or summary action, plus 6 minutes per creation action, based on Microsoft WorkLab research. Assisted value multiplies those hours by an hourly rate that defaults to $72 and is admin-configurable. It's a modeled estimate, not measured time. Present it that way and it holds up. Present it as measured savings and a CFO will take it apart.

Satisfaction rate needs at least 30 responses from at least 5 unique users before it renders.

### 14. Agent Dashboard

| | |
| --- | --- |
| **Where** | Viva Insights web app > **Agent Dashboard** |
| **What it shows** | Active agents, active users, agent responses, sessions, total credits used on agents, returning agent users, and the share of Copilot users who touch agents. Spotlights the most popular, most shared, and most versatile agents. Filters by creator type (user, org, Microsoft, third party) and by source (Agent Builder, Copilot Studio, SharePoint, Agents Toolkit). |
| **Requires** | 50 or more Copilot licenses with agent activity. Managers do not get access, unlike the Copilot Dashboard. |
| **Two views** | The Copilot Agent view covers agents inside Microsoft Copilot with 6 months of history. The Agent 365 view covers agents across all M365 apps and needs Agent 365 licensing. |
| **Status** | **Preview** |
| **Docs** | [Agent Dashboard](https://learn.microsoft.com/en-us/viva/insights/org-team-insights/agent-dashboard) |

### 15. Consumption Dashboard

| | |
| --- | --- |
| **Where** | Viva Insights web app > **Consumption Dashboard** |
| **What it shows** | **M365 services page**: active users, total Copilot credit usage, session counts, credit usage by service and org group, usage intensity by user segment (top 1%, 5%, 6 to 25%, 26 to 50%), spending policy tracking, and users at or above 90% of their limit. **GitHub page**: GitHub Copilot credits, chat requests by mode, code completions, and model usage. |
| **Coverage note** | Consumption data currently covers Copilot Cowork and the Work IQ API only. |
| **Status** | M365 services page GA. GitHub page **Preview**. |
| **Docs** | [Consumption dashboard](https://learn.microsoft.com/en-us/viva/insights/org-team-insights/ai-cost-dashboard) |

This is where you catch cost problems while they're still small. The "users near their spending limit" view is the one to check weekly.

### 16. Copilot Analytics reports

| | |
| --- | --- |
| **Where** | Viva Insights web app > Reports > **Copilot Analytics reports** |
| **What it shows** | Prebuilt Power BI reports. The **Copilot Studio agents report** covers conversational and autonomous agents built in Copilot Studio, with active agents, engaged sessions, success rate, satisfaction score, and top 5 agents. A **Sales agent adoption report** is also available. |
| **Requires** | 50 or more Copilot licenses, at least one Copilot Studio license, and agents running in the production default environment. |
| **Doesn't cover** | Declarative agents from Copilot Studio, Agent Builder agents, or SharePoint-built agents. |
| **Docs** | [Copilot Analytics reports](https://learn.microsoft.com/en-us/viva/insights/org-team-insights/copilot-analytics-reports) and the [Copilot Studio agents report](https://learn.microsoft.com/en-us/viva/insights/advanced/analyst/templates/copilot-studio-agents) |

### 17. Advanced analysis and the analyst workbench

| | |
| --- | --- |
| **Where** | Viva Insights web app > **Create analysis** |
| **What it shows** | Custom person, meeting, group-to-group, and consumption queries against the Copilot metric library. Metrics cover adoption and licensing, usage and engagement, Copilot Chat, and per-app activity for Teams, Outlook, Word, Excel, PowerPoint, OneNote, and Loop. Outputs to CSV or Power BI templates. |
| **Requires** | Insights Analyst role and a Viva Insights license |
| **Docs** | [Copilot query](https://learn.microsoft.com/en-us/viva/insights/advanced/analyst/copilot-query), [person query](https://learn.microsoft.com/en-us/viva/insights/advanced/analyst/person-query), and the full [metric reference](https://learn.microsoft.com/en-us/viva/insights/advanced/reference/metrics) |

Use this when you need to correlate Copilot usage with an org attribute the dashboard won't slice by. It's also the only way to answer questions like "did meeting hours drop for the people who adopted Copilot in Teams."

### 18. Sentiment: Viva Glint and Viva Pulse

| | |
| --- | --- |
| **What it shows** | A Copilot Impact survey template covering four questions on productivity, speed, effort, and quality. Results feed the Sentiment section of the Copilot Dashboard and render as a heat map by org attribute. |
| **Requires** | 50 or more Copilot or Viva Insights licenses for the Pulse and Glint integration. Minimum group size applies. |

Usage tells you people clicked. Sentiment tells you whether it helped. You need both, and the second one is what executives remember.

---

## Section 4: Agents

### 19. Agent Registry

| | |
| --- | --- |
| **Where** | Admin center > **Agents** > All Agents > **Registry** |
| **What it shows** | Every agent in the tenant, categorized as Microsoft-built, external partner, published by your org, or shared by a user. Columns for publisher type, platform, channel, creation date, and availability. Summary cards for total agents, agents without owners, and unmanaged agents. Covers Copilot Studio, Agent Builder, SharePoint, AI Foundry, Agents Toolkit, and third-party platforms including Amazon Bedrock and Google Vertex AI. |
| **Actions** | Enable, disable, assign, block, remove, upload a custom manifest, manage pinned agents, export to CSV |
| **Requires** | Microsoft 365 Copilot, Microsoft Agent 365, or M365 E7. Global Admin or AI Administrator. |
| **Status** | Agent 365 went GA May 1, 2026 |
| **Docs** | [Agent registry](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/agent-registry) |

The "agents without owners" card is the one to act on. Ownerless agents are the shadow IT of the agent era.

### 20. Agent Map

| | |
| --- | --- |
| **Where** | Admin center > Agents > All Agents > **Map** |
| **What it shows** | Cluster visualization of agents grouped by build platform, with cards for total agents, agents at risk, agents without owners, and unmanaged agents. Drill into any agent. |
| **Limitation** | The usage filter only works in tenants with fewer than 4,000 agents. |
| **Docs** | [Agent map](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/agent-map) |

### 21. Agent Overview

| | |
| --- | --- |
| **Where** | Admin center > Agents > **Overview** |
| **What it shows** | 30-day snapshot of agent activity, usage trends, governance gaps, pending approval requests, ownerless agents, and top 5 agent platforms. |
| **Docs** | [Agent 365 overview](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/agent-365-overview) |

### 22. Copilot Studio agent analytics

| | |
| --- | --- |
| **Where** | [copilotstudio.microsoft.com](https://copilotstudio.microsoft.com) > open an agent > **Analytics** |
| **What it shows** | For conversational agents: daily and monthly active users, conversation outcomes split into resolved, escalated, abandoned, and unengaged, CSAT, sentiment, thumbs up and down with comments, knowledge source performance, and up to 3 custom metrics you define in natural language. For autonomous agents: run counts, success and failure rates, and trigger performance. |
| **Note** | Active user metrics require authentication enabled on the agent. |
| **Docs** | [Copilot Studio analytics](https://learn.microsoft.com/en-us/microsoft-copilot-studio/analytics-overview) |

Per-agent, not tenant-wide. For the tenant view, use the Agent Registry and Agent Dashboard.

### 23. Copilot Studio credit consumption

| | |
| --- | --- |
| **Where** | [admin.powerplatform.microsoft.com](https://admin.powerplatform.microsoft.com) > Licensing > **Capacity add-ons**. Also Azure Cost Management for pay-as-you-go. |
| **What it shows** | Copilot Credit allocation, consumption, and overage against purchased packs, by tenant and environment. |
| **Naming** | Microsoft renamed Copilot Studio "messages" to **Copilot Credits** on September 1, 2025. Older documentation and blog posts still say messages. |
| **Docs** | [Copilot Studio licensing](https://learn.microsoft.com/en-us/microsoft-copilot-studio/billing-licensing) |

### 24. Power Platform admin center analytics

| | |
| --- | --- |
| **Where** | [admin.powerplatform.microsoft.com](https://admin.powerplatform.microsoft.com) |
| **What it shows** | Power Apps and Power Automate usage analytics, Dataverse capacity, environment inventory, and DLP policy state. |

A note on the **Power Platform CoE Starter Kit**: Microsoft's own documentation now states it is no longer actively maintained. It's still widely deployed and still useful, but don't build a new governance program on it without knowing that.

### 25. Azure AI Foundry

| | |
| --- | --- |
| **Where** | [ai.azure.com](https://ai.azure.com) |
| **What it shows** | Agent monitoring dashboard, tracing, built-in evaluators for groundedness and relevance, and token and cost telemetry through Azure Monitor and Cost Management. |

Where your custom-built agents report in, as opposed to the ones built in Copilot Studio or Agent Builder.

---

## Section 5: Content readiness, the reports that decide what Copilot can see

Copilot honors permissions. That's the problem. If a file is shared with everyone, Copilot will happily find it and quote it in a summary. These reports are how you find that before your CFO does.

### 26. Data Access Governance (DAG) reports

| | |
| --- | --- |
| **Where** | SharePoint admin center > Reports > **Data access governance** |
| **What it shows** | **Snapshot reports**: site permissions across all sites, sites with the broadest access, all sites a specific user can reach, and sites holding files with a given sensitivity label. **Activity reports** (28 days): sites with the most sharing links created, and sites shared with "Everyone except external users." |
| **Requires** | SharePoint Advanced Management for full features. M365 E5 gets activity reports capped at 10,000 sites, with no snapshot reports and no remediation actions. |
| **Docs** | [Data access governance reports](https://learn.microsoft.com/en-us/sharepoint/data-access-governance-reports) |

Run the EEEU report before your first Copilot pilot. Every time.

### 27. SharePoint Agent Insights

| | |
| --- | --- |
| **Where** | SharePoint admin center > Reports > **Agent Insights** |
| **What it shows** | Recently created agents across all SharePoint and OneDrive sites, top 100 sites by agent count, site template, and governance policy status. Apply Restricted Access Control or Restricted Content Discovery straight from the report. |
| **History** | 1, 7, 14, or 28 days |
| **Requires** | SharePoint Advanced Management or a Microsoft Copilot license. Without SAM you must turn on data collection first and wait 24 hours. |
| **PowerShell** | `Start-SPOCopilotAgentInsightsReport`, `Get-SPOCopilotAgentInsightsReport` |
| **Docs** | [Insights on SharePoint agents](https://learn.microsoft.com/en-us/sharepoint/insights-on-sharepoint-agents) |

### 28. SharePoint Advanced Management, the rest of it

| Feature | What it does |
| --- | --- |
| **Content Management Assessment** | Runs the key reports together and produces a Copilot readiness view with recommendations. Re-run every 30 days. |
| **Restricted Content Discovery (RCD)** | Hides a site from Copilot and org-wide search without changing permissions. |
| **Restricted Access Control (RAC)** | Locks a site to specific security groups. |
| **Site ownership and inactive site policies** | Finds ownerless and dormant sites and pushes owners to act. |
| **Site attestation** | Makes owners confirm permissions and sharing on a schedule. |
| **Change history reports** | Site setting changes over the last 180 days. |
| **App insights** | Non-Microsoft apps reaching into SharePoint content. |

Docs: [SharePoint Advanced Management](https://learn.microsoft.com/en-us/sharepoint/advanced-management) and [get ready for Copilot with SAM](https://learn.microsoft.com/en-us/microsoft-365/copilot/get-ready-copilot-sharepoint-advanced-management).

RCD is the fastest lever you have. When a site is a known oversharing problem and you can't fix permissions this quarter, RCD takes it out of Copilot's reach today.

---

## Section 6: Microsoft Purview, the security and compliance view

Portal: [purview.microsoft.com](https://purview.microsoft.com)

Purview groups AI apps into three buckets, and this decides what you can see and what you pay for:

| Category | Includes | Cost |
| --- | --- | --- |
| **Copilot experiences and agents** | M365 Copilot, Security Copilot, Copilot in Fabric, Copilot Studio, Cowork | Included in your M365 or Purview license |
| **Enterprise AI apps** | Entra-registered AI apps, Microsoft Foundry, ChatGPT Enterprise, Claude Enterprise | Pay-as-you-go, Azure subscription required |
| **Other AI apps** | Consumer ChatGPT, Gemini, DeepSeek, and thousands more | Pay-as-you-go, plus device onboarding and the Purview browser extension |

### 29. DSPM for AI

| | |
| --- | --- |
| **Where** | Purview > Solutions > **DSPM for AI** |
| **What it shows** | Total AI interactions over time, sensitive info types detected in AI prompts, unethical behavior detections sourced from Communication Compliance, and insider risk severity for AI usage. Activity Explorer drills to individual events with the user, app, AppHost, sensitive info types, and the files referenced including their sensitivity labels. An apps and agents inventory shows what data each agent touches. Weekly data risk assessments scan your top 100 SharePoint sites. |
| **Also does** | One-click policy creation for unethical behavior detection, sensitive info in Copilot interactions, and Copilot interaction retention. |
| **Requires** | M365 E3 or above with Audit on for Copilot experiences. Pay-as-you-go for enterprise and other AI apps. Reading actual prompt content needs the Content Explorer Content Viewer or Purview Data Security AI Content Viewer role, which standard admin roles do not include. |
| **Version note** | There are two versions. **DSPM for AI (classic)**, formerly the AI Hub, still works but gets no new features. The newer **Data Security Posture Management** adds data security objectives, third-party cloud coverage, and AI observability. Build new work on the new one. |
| **Docs** | [DSPM for AI](https://learn.microsoft.com/en-us/purview/dspm-for-ai) and [DSPM](https://learn.microsoft.com/en-us/purview/data-security-posture-management-learn-about) |

Start here for the "is anyone pasting patient data into ChatGPT" question. Seeing third-party AI apps requires pay-as-you-go billing and device onboarding, so budget for it before you promise the answer.

### 30. Purview Audit for Copilot

| | |
| --- | --- |
| **Where** | Purview > Solutions > **Audit** > Search |
| **What it shows** | The `CopilotInteraction` record type captures `AppHost` (which surface), `AppIdentity`, `AgentId` and `AgentName`, and `AccessedResources`, an array of every file and email Copilot touched to build the answer, including each item's sensitivity label. Also flags `JailbreakDetected` and `XPIADetected` for prompt injection. Separate record types cover connected enterprise AI apps and third-party AI apps. |
| **Retention** | Audit Standard 180 days. Audit Premium 1 year for Entra, Exchange, OneDrive, and SharePoint. 10 years with the add-on. |
| **How to query** | Purview portal, `Search-UnifiedAuditLog` in Exchange Online PowerShell, the Graph audit query API, or the Office 365 Management Activity API for SIEM. |
| **Docs** | [Audit logs for Copilot](https://learn.microsoft.com/en-us/purview/audit-copilot) |

**Two things people get wrong here.**

Prompt and response text is not in the audit log. You get metadata about the interaction and what it accessed. For the actual text, use eDiscovery or Activity Explorer with the right role.

Microsoft states plainly that the audit log is not a usage reporting source. Counts you build from audit data will not match the Copilot usage report. Use the usage reports for adoption metrics and the audit log for investigations.

### 31. eDiscovery for Copilot interactions

| | |
| --- | --- |
| **Where** | Purview > Solutions > **eDiscovery** |
| **What it shows** | Copilot prompts and responses stored in a hidden folder in each user's Exchange Online mailbox, with item classes like `IPM.SkypeTeams.Message.Copilot.*`. Search by custodian against Exchange, then hold, review, and export. |
| **Requires** | E3 for search, hold, and export. E5 or E5 Compliance for review sets, conversation threading, decryption, and analytics. |
| **Heads up** | Classic eDiscovery and Content Search retired August 31, 2025 everywhere except 21Vianet. |
| **Docs** | [eDiscovery](https://learn.microsoft.com/en-us/purview/edisc) |

### 32. The rest of the Purview stack

| Solution | What it gives you for Copilot | License |
| --- | --- | --- |
| **Communication Compliance** | A generative AI policy template that inspects prompts and responses for policy violations. Feeds the DSPM unethical behavior view. | E5 or E5 Compliance |
| **Insider Risk Management** | Risky AI usage and Risky Agents templates covering sensitive data in prompts and AI site visits. The Risky Agents template now applies by default (Preview). | E5 or E5 Compliance |
| **Data Loss Prevention** | A Microsoft 365 Copilot DLP location that can stop labeled content from being processed. Alerts land in the DLP alerts dashboard. | E3 and up for the Copilot location |
| **Data Lifecycle Management** | Retention for Copilot interactions, which decides how long anything is discoverable at all. | E3 and up |
| **Activity Explorer / Content Explorer** | Label and DLP activity, and where labeled content lives. Activity Explorer shows 30 days, so go to the audit log for older data. | E3 and up |
| **Compliance Manager** | Assessment templates for EU AI Act, ISO 42001, and NIST AI RMF, with scored improvement actions. | 3 premium templates free with E5 |
| **Data Security Investigations** | Deep investigation over exfiltrated sensitive data, including AI-driven risk categories. | Pay-as-you-go |

**One current gap worth knowing.** DLP alerts generated only from Endpoint DLP, Teams DLP, or M365 Copilot DLP are not evaluated by the DLP alert indicator in Insider Risk Management. If you assumed Copilot DLP hits would raise insider risk scores, they don't yet.

### 33. Defender for Cloud Apps, shadow AI discovery

| | |
| --- | --- |
| **Where** | [security.microsoft.com](https://security.microsoft.com) > Cloud apps > **Cloud discovery** |
| **What it shows** | Discovered generative AI apps in use across the org, with risk scores from the cloud app catalog, user counts, and traffic volume. |
| **Note** | File policies in Defender for Cloud Apps retire January 6, 2027. Move that logic to Purview DLP or auto-labeling. |
| **Docs** | [Discovered apps](https://learn.microsoft.com/en-us/defender-cloud-apps/discovered-apps) |

### 34. Microsoft Entra

| | |
| --- | --- |
| **Where** | [entra.microsoft.com](https://entra.microsoft.com) > Entra ID > Monitoring & health |
| **What it shows** | Sign-in logs filtered to Copilot applications, Usage & insights for per-app sign-in activity, and audit logs. **Entra Agent ID** adds agent-aware logging with an `agentType` field distinguishing agent blueprints, agent instances, and agent user accounts, plus a `blueprintId` to tie an instance back to its definition. |
| **Retention** | 30 days in the portal. Export to Log Analytics, storage, or Event Hub for longer. |
| **Status** | Entra Agent ID logs GA. The Graph API for agent sign-ins is on the beta endpoint. |
| **Docs** | [Entra Agent ID logs](https://learn.microsoft.com/en-us/entra/agent-id/sign-in-audit-logs-agents) |

### 35. Security Copilot usage

| | |
| --- | --- |
| **Where** | [securitycopilot.microsoft.com](https://securitycopilot.microsoft.com) > Owner settings > **Usage monitoring** |
| **What it shows** | Up to 90 days of Security Compute Unit consumption by session, user, plugin, category, and experience, with Excel export and capacity warnings. |
| **Requires** | Copilot owner role. SCU capacity provisioned in Azure. |
| **Docs** | [Manage SCU usage](https://learn.microsoft.com/en-us/copilot/security/manage-usage) |

---

## Section 7: APIs, when the portal isn't enough

### 36. Microsoft Graph reporting APIs

Use these when you need Copilot numbers in Power BI, a warehouse, or a scheduled export.

**The current path** is `https://graph.microsoft.com/v1.0/copilot/reports/`. The older `/reports/getMicrosoft365Copilot...` endpoints in beta still work, but Microsoft's docs point you at the `/copilot` path going forward.

| Endpoint | Returns |
| --- | --- |
| `getMicrosoft365CopilotUsageUserDetail(period, version)` | Per-user Copilot activity. Pass `version='v2'` for prompts submitted, active days, Edge, Copilot Chat work and web, and Copilot agent last activity date. |
| `getMicrosoft365CopilotUserCountSummary(period)` | Active and enabled user counts for the period |
| `getMicrosoft365CopilotUserCountTrend(period)` | Daily trend of active and enabled users |
| `getTeamsUserActivityUserDetail(period)` | Teams activity per user, useful as a Copilot readiness denominator |

Period values: `D7`, `D30` or `D28`, `D90`, `D180`, `ALL`. Permission: `Reports.Read.All`.

**For raw prompt and response export**, use the AI interaction history API:

```http
GET https://graph.microsoft.com/v1.0/copilot/users/{id}/interactionHistory/getAllEnterpriseInteractions
```

Requires the `AiEnterpriseInteraction.Read.All` application permission. There is no delegated option. Copilot Studio agent interactions are excluded.

**PowerShell.** There are no dedicated cmdlets wrapping the new `/copilot/reports/` endpoints yet. Call them directly:

```powershell
Connect-MgGraph -Scopes "Reports.Read.All"
Invoke-MgGraphRequest -Uri "https://graph.microsoft.com/v1.0/copilot/reports/getMicrosoft365CopilotUsageUserDetail(period='D30',version='v2')" -OutputFilePath "copilot-report.csv"
```

Docs: [Copilot reports API](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/reports/resources/copilotreportroot) and [AI interaction history](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/interaction-export/aiinteractionhistory-getallenterpriseinteractions).

---

## How to get access

The internal version of this kind of doc ends with an entitlement request. Yours ends with Entra roles.

### Roles for admin center usage reports

Any one of these gets you in:

- Global Administrator
- **AI Administrator** (the newer role, and the right one for most Copilot work)
- Exchange, SharePoint, Teams, or Teams Communications Administrator
- Reports Reader
- Usage Summary Reports Reader (aggregates only, no per-user data)
- User Experience Success Manager (aggregates only)

### Roles for everything else

| Surface | Role |
| --- | --- |
| Copilot Dashboard and Agent Dashboard | Global Admin, senior leader by org hierarchy, or Viva Insights Analyst with global partition access. Managers need an admin to enable them. |
| Analyst workbench | Insights Analyst, plus a Viva Insights license |
| Agent Registry, Map, Overview | Global Admin or AI Administrator |
| Purview solutions | Compliance Administrator or Global Admin. Security Reader for read-only. |
| Reading AI prompt content in Purview | Content Explorer Content Viewer, or Purview Data Security AI Content Viewer. Not included in standard admin roles. |
| SharePoint reports | SharePoint Administrator |
| Power Platform | Power Platform Administrator |

### Turn this on before you need it

Three settings decide whether your data is any good later. Do them now.

**1. Usernames are hidden by default.** Reports > Settings has a "Display concealed user, group, and site names" toggle. When it's on, every usage report shows anonymized identifiers instead of names, which makes per-user analysis useless. Turning it off is a deliberate privacy decision, so make it with your privacy and works council stakeholders rather than quietly flipping it. The Graph APIs return real identifiers regardless, which is worth knowing before you build a workaround.

**2. Audit has to be on** for DSPM for AI to show Copilot activity at all. It's on by default in most tenants. Confirm it.

**3. Minimum group size** in Viva Insights defaults to 10 and can go as low as 5. Set it before leaders start asking for team-level views, because it determines which breakdowns render at all.

---

## Retention, at a glance

The number that bites people is the shortest one in the chain.

| Data | How far back |
| --- | --- |
| Admin center usage reports | 7 / 30 / 90 / 180 days |
| Copilot agent, connectors, and credits reports | 7 or 30 days |
| Cowork usage | From April 1, 2026 |
| Copilot Dashboard | 28-day rolling window, 6 months of trend |
| Copilot Dashboard data lag | Up to 6 days |
| Agent Dashboard | 28-day window, 6 months of trend |
| Purview Activity Explorer | 30 days |
| Audit Standard | 180 days |
| Audit Premium | 1 year, or 10 years with the add-on |
| Entra sign-in logs | 30 days in portal |
| SharePoint DAG activity reports | 28 days |
| SharePoint change history | 180 days |
| Security Copilot SCU usage | 90 days |

If you need year-over-year Copilot reporting, nothing above gives it to you natively. Schedule a Graph export to your own storage now, because you can't go back and get data the platform already dropped.

---

## The gotchas

The things that cost people a rework cycle.

**The usage report and the audit log will never agree.** They measure different things and Microsoft says so directly. Use usage reports for adoption, audit for investigations. Don't let anyone build a "better" adoption metric on audit data.

**Licensed and unlicensed Copilot usage are two separate reports.** Report #1 and report #3. Pull both or you'll understate your footprint.

**Opening the Copilot pane isn't usage.** A user has to take an action. Expect your active user number to run below what adoption champions believe.

**Under 50 Copilot licenses, the Viva dashboard is materially thinner.** No agent insights, no benchmarks, no sentiment, no trendlines. Factor it into pilot sizing.

**Assisted hours are modeled, not measured.** 6 minutes per action, times an editable $72 default rate. Fine as a directional number. Dangerous as a hard ROI claim.

**Prompt text isn't where you think it is.** Not in the audit log. It's in a hidden mailbox folder, reachable through eDiscovery or Activity Explorer with a role most admins don't have.

**The old Copilot agents report is deprecated.** So is classic eDiscovery, retired August 2025. And Defender for Cloud Apps file policies retire January 6, 2027.

**The CoE Starter Kit is no longer actively maintained**, per Microsoft's own docs. Fine to keep running. Not a foundation for something new.

**Preview reports change.** As of August 2026, agent usage, connectors usage, search usage, credits, the Agent Dashboard, and the GitHub consumption page are all Preview. Schemas and field names can move.

---

## Resources

- [Microsoft 365 admin center usage reports](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/activity-reports)
- [Microsoft Copilot Dashboard](https://learn.microsoft.com/en-us/viva/insights/org-team-insights/copilot-dashboard)
- [Purview data security for generative AI](https://learn.microsoft.com/en-us/purview/ai-microsoft-purview)
- [Get ready for Copilot with SharePoint Advanced Management](https://learn.microsoft.com/en-us/microsoft-365/copilot/get-ready-copilot-sharepoint-advanced-management)
- [Microsoft Agent 365](https://learn.microsoft.com/en-us/microsoft-agent-365/overview)
- [Copilot Success Kit](https://adoption.microsoft.com/en-us/copilot/success-kit/)

Related guides here: [Copilot Governance](./copilot%20governance%20getting%20started.md) for the controls behind these reports, [Copilot Agent Billing](./copilot%20agent%20billing%2C%20credits%20and%20cost%20attribution.md) for what the credit numbers mean, and [Licensing and Deployment](./copilot%20licensing%20and%20deployment%2C%20who%20gets%20what.md) for who should have a seat.

---

Found something out of date? Open an issue. This page has a shelf life and I'd rather fix it than let it rot.

---

[Back to the Education Playground](../README.md#education-playground)
