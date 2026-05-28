# Microsoft Agent 365: Deep Technical Explanation, Licensing Model, and How to Explain It to Customers

> **Audience:** This is a practitioner reference, written for SEs, technical sellers, and IT professionals who need to explain Microsoft Agent 365 accurately to customers and stakeholders. It is not a customer-facing document — it is a field enablement resource built entirely from public Microsoft documentation. Every claim links to a public source.

## Executive Summary

**Microsoft Agent 365 is not an agent builder and it is not the runtime for agents.** It is Microsoft's **control plane for AI agents**: the product Microsoft positions for IT/security to **observe, govern, and secure** agents across the organization, from the **Microsoft 365 admin center** and adjacent security/admin surfaces.

Microsoft positions **Microsoft Copilot Studio**, **Microsoft 365 declarative/custom agents**, and **Microsoft Foundry Agent Service** as the places where agents are **built and run**. Agent 365 is the layer that manages the **agent estate** across those systems.

**Licensing is the key distinction:** Microsoft's licensing FAQ says **Agent 365 is licensed per user, not per agent**, whether you buy it standalone or as part of **Microsoft 365 E7**. It also says **agents do not require their own Agent 365 licenses**. Official pricing: **$15/user/month** standalone, **$99/user/month** for Microsoft 365 E7.

**The cleanest customer explanation:** Agent 365 is **organization-wide in control plane / management surface**, but **user-scoped in licensing entitlement**. It is a **tenant-wide management plane** with a **per-user commercial model**, not a per-agent "premium mode" that changes the agent itself.

**Sources:** [microsoft.com/en-us/microsoft-agent-365](https://www.microsoft.com/en-us/microsoft-agent-365), [learn.microsoft.com/en-us/microsoft-agent-365/overview](https://learn.microsoft.com/en-us/microsoft-agent-365/overview), [microsoft.com/licensing/faqs/122](https://www.microsoft.com/licensing/faqs/122)

---

## Bottom Line on the Mixed-Licensing Question

No public Microsoft document says that turning on Agent 365 makes a shared agent become a separately licensed "premium agent." What Microsoft documents is that Agent 365 is a **control plane** and the **license is per user**.

The safest, most defensible explanation: **the agent object stays the same; what changes is the management/control plane around it and which users/scenarios are entitled to Agent 365's premium governance/security/observability value.**

The user's **ability to use the agent** is still governed by the **underlying agent access path and runtime licensing/metering**, not by Agent 365 alone. In Microsoft 365 Copilot, agent use comes with the Copilot license, and certain interactions in Copilot Chat/Teams/SharePoint are **zero-rated** for Microsoft 365 Copilot-licensed users. For **Copilot Chat** users without Microsoft 365 Copilot, some agent types are available at no additional cost, while agents that access shared tenant data are **metered** and require billing setup.

**Where the public docs are still thin:** There is no Microsoft Learn or official licensing page that explicitly walks through **one shared agent used by both Agent 365-licensed and non-licensed end users** and says whether Agent 365 telemetry/observability is full-fleet, licensed-user-only, or something in between. The exact telemetry partitioning for a mixed-end-user scenario is **not explicitly documented in current public sources**.

---

## 1. What Microsoft Agent 365 Is

### The Three-Plane Mental Model

| Plane | What it is | Products |
|---|---|---|
| **Build** | Where agents are authored | Microsoft 365 declarative/custom agents, Microsoft Copilot Studio, Microsoft Foundry Agent Service |
| **Runtime** | Where agents execute | Microsoft 365 channels (Copilot Chat, Teams, Outlook, SharePoint), Foundry Agent Service runtime |
| **Control** | Where IT/security governs the agent estate | Microsoft Agent 365, Copilot Control System (CCS) |

### Product-by-Product Relationship to Agent 365

| Product / Framework | What it is | How Agent 365 relates |
|---|---|---|
| **Microsoft 365 agents** | Agents that extend Copilot in Microsoft 365 | Agent 365 is the control plane to observe/govern/secure them as part of the org's agent estate |
| **Microsoft Copilot Studio** | Low-code/full experience to build agents | Agent 365 does not replace Copilot Studio billing/runtime; it governs the agents after they exist in the environment |
| **Microsoft 365 Copilot Chat** | End-user chat surface with agents | Agent 365 is not the Copilot Chat runtime meter; it is the governance/security/observability plane around agents and their use |
| **Microsoft Foundry Agent Service** | Fully managed agent platform on Azure/Microsoft Foundry | Agent 365 is how Microsoft positions centralized governance/identity/security for the fleet, including agents built outside Microsoft 365-native tooling |
| **Other / third-party / non-Microsoft frameworks** | External or custom frameworks | Agent 365 can manage agents regardless of where they are built or acquired; the Agent 365 SDK explicitly supports any agent SDK or platform |

### CCS vs. Agent 365

This is one of the biggest sources of confusion in the field:

**Copilot Control System (CCS)** is the **governance framework** for Microsoft 365 Copilot and agents. It spans security and governance, management controls, and measurement/reporting for Microsoft 365 Copilot, Copilot Chat, Microsoft 365 prebuilt agents, and Copilot Studio agents published to Microsoft 365 channels.

**Microsoft Agent 365** is the **product / control plane for AI agents**: a SKU with centralized registry, lifecycle, security, and role-specific oversight for the agent estate across the organization.

**Customer-safe phrasing:** "CCS is Microsoft's overall governance framework for Copilot and Microsoft 365 agent experiences; Agent 365 is the specific control-plane product for governing the agent fleet."

---

## 2. Deep Technical Explanation: Architecture, Identity, Lifecycle, Context, Data, and Logging

### 2.1 Agent Lifecycle and Registry

Microsoft's Agent 365 overview says admins can view **all their agents in a single, centralized registry**, with unified visibility into **adoption, activity, and health**. Governance is centered around lifecycle management, access control, and compliance through the **Agent 365 registry in the Microsoft 365 admin center**, **Microsoft Entra**, and **Microsoft Purview**.

CCS management-controls documentation covers lifecycle management including visibility into **status, governance, and lifecycle of agents and connectors**, with management from **initial deployment to governance to retirement**, plus approval workflows, sharing/coauthoring rules, and DLP-based publishing restrictions.

**Engineering interpretation:** The agent inventory/lifecycle record is becoming first-class: who owns/sponsors it, where it was built, what policies apply, and whether it is still approved to run. That is a meaningful shift from the earlier "just publish a Copilot Studio bot and hope governance catches up later" model.

### 2.2 Identity and Execution Context

Microsoft Entra Agent ID is the technical foundation for agent identity. An **agent identity is a special service principal in Microsoft Entra ID**. It is created from an **agent identity blueprint**, can have a **sponsor** for human accountability, and can optionally be paired with an **agent's user account** when the agent needs a full Entra user account for authentication to systems that require it.

The most important execution-context detail:

- **Interactive agents called with a user token** acquire user tokens on behalf of the agent identity
- **Autonomous agents** acquire app tokens on behalf of the agent identity

That means the Microsoft model distinguishes two fundamental execution patterns:

1. **User-delegated / on-behalf-of (OBO)** interaction
2. **Agent-own / autonomous** interaction

The Agent 365 SDK can give agents **Entra-backed Agent Identity**, their own user resources such as **mailbox**, auditable telemetry via **OpenTelemetry**, and access to governed **MCP servers** for Microsoft 365 workloads under admin control.

### 2.3 Authorization Boundaries and Least Privilege

Microsoft's authorization guidance for Entra Agent ID says agent identities were introduced because normal app registrations or user accounts are not ideal for AI agents. Microsoft explicitly blocks agents from many **high-privilege roles or permissions** to preserve **least privilege**.

The architecture is not "an agent is just a service principal with superpowers." Microsoft is describing a **constrained identity model** for agents, with special handling because AI agents can act autonomously and at scale.

### 2.4 Data Access and Tools

For **Microsoft 365-bound agents**, data access is governed through standard Microsoft 365 / Purview / SharePoint controls. Organizations should use **Microsoft Purview** and **SharePoint Advanced Management** to identify oversharing, restrict access, apply labels, and control data exposure for Copilot and agents.

For **Foundry agents**, the Foundry runtime supports tools with managed authentication, including **service managed credentials** and **On-Behalf-Of (OBO)** authentication. Foundry can publish/share through Microsoft Teams, Microsoft 365 Copilot, and the **Entra Agent Registry**.

For **Agent 365-enabled agents**, the Agent 365 SDK documentation says agents can call governed **MCP servers** to access Microsoft 365 workloads such as **Mail, Calendar, SharePoint, and Teams** under admin control.

### 2.5 Logging, Observability, and Security Telemetry

The observability story spans the control plane and the runtime:

- **Agent 365 overview:** centralized registry, adoption/activity/health, role-specific oversight for AI admins, security leaders, and business leaders
- **Agent 365 SDK:** OpenTelemetry, audited/traceable interactions, inference events, and tool usage
- **Foundry Agent Service:** end-to-end tracing, metrics, and Application Insights integration
- **Microsoft Security Blog (GA announcement):** Agent 365 is about end-to-end observability because "you can't govern what you can't see"

On the security/compliance side:

- **Purview** for information protection, DLP, and risk safeguards
- **Defender** for threat detection and real-time protection
- **Entra** for risk-based access control for users and agents acting on their behalf

---

## 3. Licensing Model: Per-User, Tenant/Global, and Separate Runtime Consumption

### The Most Important Licensing Distinction

Agent 365 licensing is **not** the same as Copilot Studio runtime consumption and **not** the same as Microsoft 365 Copilot user licensing. Public Microsoft docs show three separate commercial layers:

1. **Microsoft Agent 365**: per-user control-plane license; agents do not need their own licenses; official pricing is **$15/user/month**; no consumption-based cost for Agent 365 yet
2. **Microsoft 365 Copilot**: per-user productivity/agent usage license for Microsoft 365 experiences; some agent usage in Microsoft 365 channels is included/zero-rated
3. **Copilot Studio / Copilot Chat metering**: PAYG / prepaid / Copilot Credits for certain agent scenarios, especially for Copilot Chat users and for agents that access tenant data or use more advanced orchestration/actions

### What Microsoft Explicitly Says Publicly

- Agent 365 is licensed **per user**, not per agent
- **Agents do not require their own Agent 365 licenses**
- Agent 365 can be bought standalone or through **Microsoft 365 E7**
- Microsoft 365 Copilot-licensed users get agent use in Microsoft 365 channels, and certain interactions are **zero-rated** in Copilot Chat / Teams / SharePoint
- Copilot Chat users can use some agents at **no additional cost**, but agents that access **shared tenant data** are **metered** and require billing setup via Microsoft 365 admin center or Power Platform admin center

### Why This Matters for Customer Explanations

A common misconception is conflating these into a single statement like "Agent 365 premium is an all-or-nothing tenant switch." It is not. The more precise explanation:

- **Agent 365** = control plane / governance / security / observability layer
- **Microsoft 365 Copilot / Copilot Chat / Copilot Studio** = user experience + build/runtime + consumption/licensing mechanics

---

## 4. Mixed Licensing Scenario: One Preexisting Shared Agent, Some Users Licensed, Some Not

### First Principle: The Agent Does Not Become a Different Agent

Microsoft's public docs describe Agent 365 as a **control plane** and say that **agents do not require their own licenses**. There is no public Microsoft documentation saying that assigning Agent 365 to some users transforms the existing agent into a different "premium" artifact or strips access from users who otherwise still have access through the underlying channel/product path.

**The agent itself is best understood as unchanged.** What changes is the **control-plane coverage / entitlement / management posture** around that agent and its use, not the fundamental existence of the shared agent object itself.

### Second Principle: The User's Ability to Use the Agent Still Depends on the Underlying Path

- For **Microsoft 365 Copilot licensed users**, agent use comes with that license, and certain usage is zero-rated in Microsoft 365 channels
- For **Copilot Chat** users, some agents (instructions + public websites only) are no-additional-cost, but agents that access tenant data are metered and require billing setup

Agent 365 is not the gate that determines whether the user can invoke the shared agent. That still depends on Copilot / Copilot Chat / Teams / SharePoint / Copilot Studio access and metering rules.

### Third Principle: Agent 365 Entitlement is Per-User

The official Microsoft licensing FAQ says Agent 365 is **per user**, not per agent, and is tied to the user associated with the agent use case.

**Defensible customer statement:** "One shared agent can continue to be shared, but Agent 365 entitlement attaches to the users/scenarios you license. Agent 365 does not appear in the public docs as a per-agent runtime license that automatically forces every end user of that shared agent into the paid entitlement."

---

## 5. Table 1: Licensed Agent 365 User vs. Unlicensed User Interacting with the Same Shared Agent

> **Important note:** cells marked **"public docs unclear"** mean Microsoft's public documentation did not explicitly answer that exact mixed-user shared-agent question in the sources reviewed. It does **not** automatically mean the platform lacks the capability; it means the public docs do not yet spell it out. All gaps noted here are documentation gaps, not product gaps.

| Dimension | Licensed Agent 365 User | Unlicensed User | What Microsoft Explicitly Documents |
|---|---|---|---|
| **Does the agent itself change?** | No public doc says the agent becomes a "premium agent." | Same. The agent object does not change because only some users are Agent 365-licensed. | Agent 365 is the control plane; agents do not require their own licenses. |
| **Can the user still use the shared agent?** | Yes, subject to the underlying channel/license path. | Also subject to the underlying channel/license path. | Copilot Chat and Microsoft 365 Copilot docs govern user access and metering, not Agent 365 alone. |
| **Agent 365 entitlement** | Yes, this user is within the per-user Agent 365 license scope. | No, this user is not within the per-user Agent 365 license scope. | Agent 365 is licensed per user, not per agent. |
| **Microsoft 365 Copilot zero-rated agent usage** | If the same user also has Microsoft 365 Copilot, certain usage in Copilot Chat / Teams / SharePoint is zero-rated. | Not unless that user also has Microsoft 365 Copilot. | Zero-rated usage is tied to the Microsoft 365 Copilot user license, not Agent 365. |
| **Copilot Chat no-cost vs. metered behavior** | Depends on whether the agent is declarative/public-web only or accesses tenant data. | Same dependency. | Copilot Chat users can use some agents at no extra cost; tenant-data / metered scenarios require billing setup. |
| **Observability / telemetry in Agent 365 dashboards** | Public docs clearly promise centralized registry, adoption/activity/health, and role-specific oversight. | **Public docs unclear** on whether shared-agent interaction telemetry is partitioned by licensed vs. unlicensed end-user interactions. | Centralized registry and role-specific oversight are documented; mixed-user telemetry scope is not explicitly documented in public sources reviewed. |
| **Security / compliance controls** | Agent 365 + Entra + Purview + Defender are documented for managed agents and agents acting on behalf of users. | **Public docs unclear** on how Microsoft documents end-user entitlement boundaries for the same shared agent, but core platform controls are described at the agent/tenant/platform level. | Entra risk-based controls, Purview DLP/information protection, and Defender protections are documented for agents and Copilot/agent workloads broadly. |
| **Blind-spot risk in a mixed user population** | Lower entitlement ambiguity for licensed users. | **Documentation ambiguity**, not necessarily platform blindness. | Public docs do not explicitly provide a mixed-user shared-agent observability matrix. |

---

## 6. Table 2: Tenant-Level / Agent-Wide Features vs. User-Level Licensed Features

| Scope | Feature / Capability | What Microsoft Publicly Documents |
|---|---|---|
| **Tenant / org-wide / agent-estate** | Centralized registry of agents, with adoption/activity/health visibility | Admins can view all agents in a centralized registry, with role-specific oversight for different leaders/admins. |
| **Tenant / org-wide / agent-estate** | Lifecycle management (status, governance, deployment, retirement) | CCS management controls covers lifecycle from deployment to retirement, including approval workflows, sharing/coauthoring controls, and DLP publishing restrictions. |
| **Tenant / org-wide / agent-estate** | Security and governance controls for Copilot and agents | CCS security-and-governance docs describe data security, AI security, and compliance/privacy controls using Microsoft 365 admin center, SharePoint Advanced Management, Purview, and Defender. |
| **Tenant / org-wide / runtime/billing config** | PAYG / metering setup for Copilot Chat or Copilot Studio | Admins can set up pay-as-you-go / prepaid / Azure billing for Copilot Chat and Copilot Studio consumption scenarios. |
| **Per user** | Agent 365 license assignment | Official licensing FAQ says Agent 365 is per user, not per agent. |
| **Per user** | Microsoft 365 Copilot included/zero-rated usage for certain agent interactions | Microsoft 365 Copilot licensed users get zero-rated usage for classic answers, generative answers, and Graph tenant grounding in Microsoft 365 channels. |
| **Per user** | Copilot Chat access path to no-cost or metered agents | Some agents are no-additional-cost and others are metered for Copilot Chat users, depending on data access/capabilities. |
| **Per user / user-associated scenario** | Agent identity association / delegated context / sponsor-owner model | Official licensing FAQ ties Agent 365 to the user associated with agent usage; Entra Agent ID docs describe sponsor accountability and user-delegated vs. autonomous token flows. |

---

## 7. What Changes vs. What Does Not Change

### What Changes When Agent 365 is Enabled/Licensed

**1. The organization gets a centralized control plane.**

You get the Agent 365 registry / observe-govern-secure posture Microsoft documents: unified inventory, lifecycle, role-specific oversight, and integration with Entra/Purview/Defender controls for the managed agent environment.

**2. Licensed users/scenarios are within Agent 365 commercial entitlement.**

Because Microsoft documents Agent 365 as per-user, the users you license are the ones whose agent scenarios are clearly within that entitlement model.

**3. Security/governance posture becomes more explicit around agents.**

Microsoft documents agent identity, least privilege boundaries, DLP/information protection, and threat detection/protection for managed agents and agents acting on behalf of users.

### What Does Not Change

**1. The agent is still built/run where it was built/run.**

If it is a Copilot Studio agent, Copilot Studio remains the builder/runtime/billing engine. If it is a Foundry agent, Foundry remains the runtime. Agent 365 does not replace those services.

**2. The agent does not need its own Agent 365 license.**

Microsoft's official licensing FAQ explicitly says agents do not require their own licenses.

**3. Runtime consumption mechanics do not disappear.**

Copilot Studio still uses Copilot Credits / PAYG / prepaid models for the relevant scenarios, and Copilot Chat metered agent scenarios still require billing configuration where applicable.

**4. Base data access rules do not become looser.**

Microsoft documents that access should remain bounded by Entra, Purview, and least-privilege controls. The platform is not described as letting agents or users bypass those controls because Agent 365 exists.

---

## 8. Governance, Security, Observability, Auditing, and Where the Blind Spots May Be

### What Microsoft Clearly Documents

Microsoft publicly documents an **org-wide** control-plane story:

- Centralized registry and role-specific oversight in Agent 365
- Identity and lifecycle control via Entra Agent ID and sponsorship/blueprints
- Purview DLP, information protection, and oversharing controls for Copilot and agents
- Defender threat detection / real-time protection / "shadow AI" expansion in preview announcements

### What Microsoft Does Not Explicitly Spell Out in Public Docs

There is no public Microsoft article that says, for example: "If one shared agent is used by 500 people and only 100 of them have Agent 365, the Agent 365 portal will show telemetry for X but not Y."

That exact entitlement/telemetry partitioning is **not explicitly documented** in the public sources reviewed. Promising customers that the public docs already prove zero visibility blind spots in a mixed shared-agent scenario would be overstating what the documentation supports.

### Best Technical Reading of the Public Material

**Enforcement and visibility are not the same thing.** Microsoft's docs describe many controls as platform/tenant/agent-estate controls (identity, DLP, access control, lifecycle, threat protection), while licensing is described as per-user. That suggests:

- **Enforcement / guardrails** = often agent/tenant/platform scoped
- **Commercial entitlement** = per-user
- **Observability scope in mixed shared-agent scenarios** = public docs not explicit enough yet to make a hard promise

---

## 9. GA vs. Preview / Roadmap Behavior

### Clearly Documented as GA (as of May 1, 2026)

- **Microsoft Agent 365 GA date:** May 1, 2026, commercial, per-user basis
- **Official pricing:** $15/user/month standalone, or included in Microsoft 365 E7
- **Control plane positioning:** observe, govern, and secure agents across the organization

### Clearly Documented as Preview / Expanding

- Observability/governance/security for agents operating **independently with their own credentials and permissions**
- Discovery of agents and **shadow AI** using Defender and Intune for local/cloud agents
- **Windows 365 for Agents** and expanded SaaS ecosystem coverage

### Why This Matters

The identity architecture for autonomous/own-access agents is already visible in Entra Agent ID docs (agent identity, autonomous app tokens, optional agent's user account), but the **full commercial/control-plane story for independently credentialed agents is still evolving** in public documentation. That is the right way to explain the current state without overpromising.

---

## 10. How to Explain This to Customers

### 30-Second Executive Explanation

> **Microsoft Agent 365 is Microsoft's control plane for AI agents.** It is the layer IT and security use to see, govern, and secure agents across the company. It is **not** the tool that builds the agent and it is **not** the runtime meter. Those remain in products like Microsoft 365 agents, Copilot Studio, and Foundry. Commercially, Agent 365 is **licensed per user, not per agent.**

### 60-Second IT Director Explanation

> Think in **three planes**: **build**, **run**, and **govern**. You build agents in Copilot Studio or Foundry (or Microsoft 365 agent tooling), they run in Microsoft 365 channels or Foundry runtime, and **Agent 365** is the cross-estate governance/security/observability plane over that fleet. Microsoft's public docs show the management plane is centralized, but the **license is assigned per user**, not to the agent object itself.

### Precise Answer to the Mixed-Licensing Objection

> Agent 365 is **not** an all-or-nothing per-agent "premium switch." The public docs show it as a **tenant-wide management/control plane** with a **per-user licensing model**. A shared agent can still exist, while Agent 365 entitlement attaches to the users/scenarios you license. What the public docs do **not** yet spell out clearly is the exact telemetry/visibility partitioning for one shared agent used by both licensed and unlicensed end users. Avoid promising more than the documentation currently says.

---

## 11. Crisp Answer to the Original Concern

### If You Have One Preexisting Shared Agent and Only Some Users Get Agent 365

- **The agent itself does not appear to change** in public Microsoft docs; Agent 365 is documented as the control plane, not the new runtime identity of the agent artifact.
- **Licensed users** are clearly within Agent 365's commercial entitlement model.
- **Unlicensed users** may still be able to use the shared agent **if** their underlying Copilot/Copilot Chat/channel rights and metering path allow it. Agent 365 is not documented as the runtime gate for that shared agent by itself.
- **The unresolved public-doc question** is exactly how Microsoft scopes premium telemetry/observability for mixed-user usage of that same shared agent. The public docs do not yet give an explicit matrix for that case.

### The Safest Customer Statement

> **Agent 365 is tenant-wide as a management/control plane, but user-based as a license.** It does not look like a per-agent premium switch in the public docs, and Microsoft has not yet publicly documented the exact observability partitioning for mixed licensed/unlicensed usage of a shared agent.

---

## Key Sources

- [microsoft.com/en-us/microsoft-agent-365](https://www.microsoft.com/en-us/microsoft-agent-365)
- [learn.microsoft.com/en-us/microsoft-agent-365/overview](https://learn.microsoft.com/en-us/microsoft-agent-365/overview)
- [learn.microsoft.com/en-us/microsoft-agent-365/](https://learn.microsoft.com/en-us/microsoft-agent-365/)
- [microsoft.com/licensing/faqs/122](https://www.microsoft.com/licensing/faqs/122)
- [learn.microsoft.com/en-us/microsoft-365/copilot/agent-essentials/m365-agents-faq](https://learn.microsoft.com/en-us/microsoft-365/copilot/agent-essentials/m365-agents-faq)
- [learn.microsoft.com/en-us/azure/foundry/agents/overview](https://learn.microsoft.com/en-us/azure/foundry/agents/overview)
- [learn.microsoft.com/en-us/microsoft-copilot-studio/billing-licensing](https://learn.microsoft.com/en-us/microsoft-copilot-studio/billing-licensing)
- [learn.microsoft.com/en-us/copilot/agents](https://learn.microsoft.com/en-us/copilot/agents)
- [learn.microsoft.com/en-us/microsoft-365/copilot/copilot-control-system/overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-control-system/overview)
- [microsoft.com/en-us/security/blog/2026/05/01/microsoft-agent-365-now-generally-available-expands-capabilities-and-integrations/](https://www.microsoft.com/en-us/security/blog/2026/05/01/microsoft-agent-365-now-generally-available-expands-capabilities-and-integrations/)
- [learn.microsoft.com/en-us/microsoft-agent-365/developer/](https://learn.microsoft.com/en-us/microsoft-agent-365/developer/)
