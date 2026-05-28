# Microsoft Agent 365: Licensing, Architecture, and How It Fits Into Your AI Strategy

> **About this document:** This is a technical reference built entirely from public Microsoft documentation. Every claim links to a public source. It covers what Agent 365 is, how licensing works, and how it relates to Copilot Studio, Copilot Chat, and Foundry — including the mixed-licensing questions that come up most often.

---

## Executive Summary

**Microsoft Agent 365 is not an agent builder and it is not the runtime for agents.** It is Microsoft's **control plane for AI agents**: the product IT and security teams use to **observe, govern, and secure** agents across the organization, from the **Microsoft 365 admin center** and adjacent security/admin surfaces.

Microsoft builds and runs agents through **Microsoft Copilot Studio**, **Microsoft 365 declarative/custom agents**, and **Microsoft Foundry Agent Service**. Agent 365 is the layer that manages the **agent estate** across those systems.

**The key licensing point:** Microsoft's licensing FAQ says **Agent 365 is licensed per user, not per agent**, whether you buy it standalone or as part of **Microsoft 365 E7**. **Agents do not require their own Agent 365 licenses.** Official pricing: **$15/user/month** standalone, **$99/user/month** for Microsoft 365 E7.

**The short version:** Agent 365 is **organization-wide as a management surface**, but **user-scoped as a license**. It is a tenant-wide control plane with a per-user commercial model, not a per-agent "premium mode" that changes the agent itself.

**Sources:** [microsoft.com/en-us/microsoft-agent-365](https://www.microsoft.com/en-us/microsoft-agent-365), [learn.microsoft.com/en-us/microsoft-agent-365/overview](https://learn.microsoft.com/en-us/microsoft-agent-365/overview), [microsoft.com/licensing/faqs/122](https://www.microsoft.com/licensing/faqs/122)

---

## The Mixed-Licensing Question

No public Microsoft document says that turning on Agent 365 makes a shared agent become a separately licensed "premium agent." Microsoft documents Agent 365 as a **control plane** with a **per-user license**.

**The agent object stays the same.** What changes is the management and control plane around it, and which users are entitled to Agent 365's governance, security, and observability value.

A user's **ability to use an agent** is governed by the **underlying agent access path and runtime licensing**, not by Agent 365 alone. In Microsoft 365 Copilot, agent use comes with the Copilot license, and certain interactions in Copilot Chat/Teams/SharePoint are **zero-rated** for Microsoft 365 Copilot-licensed users. For **Copilot Chat** users without Microsoft 365 Copilot, some agent types are available at no additional cost, while agents that access shared tenant data are **metered** and require billing setup.

**Where documentation is still evolving:** Microsoft has not yet published documentation that explicitly walks through one shared agent used by both Agent 365-licensed and non-licensed users and states whether Agent 365 telemetry/observability is full-fleet, licensed-user-only, or something in between. The exact telemetry partitioning for a mixed-user scenario is not yet documented in current public sources.

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
| **Microsoft Foundry Agent Service** | Fully managed agent platform on Azure/Microsoft Foundry | Agent 365 provides centralized governance/identity/security for the fleet, including agents built outside Microsoft 365-native tooling |
| **Other / third-party / non-Microsoft frameworks** | External or custom frameworks | Agent 365 can manage agents regardless of where they are built or acquired; the Agent 365 SDK explicitly supports any agent SDK or platform |

### CCS vs. Agent 365

These two are frequently confused:

**Copilot Control System (CCS)** is the **governance framework** for Microsoft 365 Copilot and agents. It spans security and governance, management controls, and measurement/reporting for Microsoft 365 Copilot, Copilot Chat, Microsoft 365 prebuilt agents, and Copilot Studio agents published to Microsoft 365 channels.

**Microsoft Agent 365** is the **product and control plane for AI agents**: a SKU with centralized registry, lifecycle, security, and role-specific oversight for the agent estate across the organization.

The practical distinction: CCS is Microsoft's overall governance framework for Copilot and Microsoft 365 agent experiences; Agent 365 is the specific control-plane product for governing the agent fleet.

---

## 2. Architecture, Identity, Lifecycle, Data Access, and Logging

### 2.1 Agent Lifecycle and Registry

Agent 365 gives admins a **single, centralized registry** of all agents in the organization, with unified visibility into **adoption, activity, and health**. Governance runs through the **Agent 365 registry in the Microsoft 365 admin center**, **Microsoft Entra**, and **Microsoft Purview**.

CCS management-controls documentation covers lifecycle management including visibility into the **status, governance, and lifecycle of agents and connectors**, with management from **initial deployment through retirement**, plus approval workflows, sharing/coauthoring rules, and DLP-based publishing restrictions.

The agent inventory/lifecycle record is becoming first-class: who owns/sponsors it, where it was built, what policies apply, and whether it is still approved to run. That is a meaningful shift from the earlier model where governance was an afterthought.

### 2.2 Identity and Execution Context

Microsoft Entra Agent ID is the technical foundation for agent identity. An **agent identity is a special service principal in Microsoft Entra ID**. It is created from an **agent identity blueprint**, can have a **sponsor** for human accountability, and can optionally be paired with an **agent's user account** when the agent needs a full Entra user account for authentication to systems that require it.

Two fundamental execution patterns:

1. **User-delegated / on-behalf-of (OBO):** Interactive agents called with a user token acquire user tokens on behalf of the agent identity
2. **Agent-own / autonomous:** Autonomous agents acquire app tokens on behalf of the agent identity

The Agent 365 SDK can give agents **Entra-backed Agent Identity**, their own user resources such as **mailbox**, auditable telemetry via **OpenTelemetry**, and access to governed **MCP servers** for Microsoft 365 workloads under admin control.

### 2.3 Authorization Boundaries and Least Privilege

Microsoft introduced agent identities because normal app registrations or user accounts are not well-suited for AI agents. Microsoft explicitly blocks agents from many **high-privilege roles or permissions** to preserve **least privilege**.

The architecture is built around a **constrained identity model** for agents, with special handling because AI agents can act autonomously and at scale.

### 2.4 Data Access and Tools

For **Microsoft 365-bound agents**, data access is governed through standard Microsoft 365 / Purview / SharePoint controls. Organizations can use **Microsoft Purview** and **SharePoint Advanced Management** to identify oversharing, restrict access, apply labels, and control data exposure for Copilot and agents.

For **Foundry agents**, the Foundry runtime supports tools with managed authentication, including **service managed credentials** and **On-Behalf-Of (OBO)** authentication. Foundry can publish/share through Microsoft Teams, Microsoft 365 Copilot, and the **Entra Agent Registry**.

For **Agent 365-enabled agents**, agents can call governed **MCP servers** to access Microsoft 365 workloads such as **Mail, Calendar, SharePoint, and Teams** under admin control.

### 2.5 Logging, Observability, and Security Telemetry

The observability story spans the control plane and the runtime:

- **Agent 365:** centralized registry, adoption/activity/health, role-specific oversight for AI admins, security leaders, and business leaders
- **Agent 365 SDK:** OpenTelemetry, audited/traceable interactions, inference events, and tool usage
- **Foundry Agent Service:** end-to-end tracing, metrics, and Application Insights integration
- **Microsoft Security Blog (GA announcement):** Agent 365 is built around end-to-end observability because "you can't govern what you can't see"

Security and compliance coverage:

- **Purview** for information protection, DLP, and risk safeguards
- **Defender** for threat detection and real-time protection
- **Entra** for risk-based access control for users and agents acting on their behalf

---

## 3. Licensing Model: Per-User, Tenant-Wide, and Runtime Consumption

### The Key Distinction

Agent 365 licensing is **not** the same as Copilot Studio runtime consumption and **not** the same as Microsoft 365 Copilot user licensing. There are three separate commercial layers:

1. **Microsoft Agent 365**: per-user control-plane license; agents do not need their own licenses; official pricing is **$15/user/month**; no consumption-based cost for Agent 365 yet
2. **Microsoft 365 Copilot**: per-user productivity/agent usage license for Microsoft 365 experiences; some agent usage in Microsoft 365 channels is included/zero-rated
3. **Copilot Studio / Copilot Chat metering**: PAYG / prepaid / Copilot Credits for certain agent scenarios, especially for Copilot Chat users and for agents that access tenant data or use more advanced orchestration/actions

### What Microsoft Officially Documents

- Agent 365 is licensed **per user**, not per agent
- **Agents do not require their own Agent 365 licenses**
- Agent 365 can be bought standalone or through **Microsoft 365 E7**
- Microsoft 365 Copilot-licensed users get agent use in Microsoft 365 channels, and certain interactions are **zero-rated** in Copilot Chat / Teams / SharePoint
- Copilot Chat users can use some agents at **no additional cost**, but agents that access **shared tenant data** are **metered** and require billing setup via Microsoft 365 admin center or Power Platform admin center

### Why This Matters

A common misconception is treating Agent 365 as an all-or-nothing tenant switch that changes agent behavior for everyone. That is not what Microsoft documents. The distinction is:

- **Agent 365** = control plane / governance / security / observability layer
- **Microsoft 365 Copilot / Copilot Chat / Copilot Studio** = user experience + build/runtime + consumption/licensing mechanics

---

## 4. Mixed Licensing: One Shared Agent, Some Users Licensed, Some Not

### The Agent Does Not Become a Different Agent

Microsoft describes Agent 365 as a **control plane** and states that **agents do not require their own licenses**. There is no Microsoft documentation saying that assigning Agent 365 to some users transforms the existing agent into a different "premium" artifact or removes access from users who otherwise have access through the underlying channel/product path.

**The agent itself is unchanged.** What changes is the **control-plane coverage and management posture** around that agent, not the agent object itself.

### The User's Ability to Use the Agent Still Depends on the Underlying Path

- For **Microsoft 365 Copilot licensed users**, agent use comes with that license, and certain usage is zero-rated in Microsoft 365 channels
- For **Copilot Chat** users, some agents (instructions + public websites only) are no-additional-cost, but agents that access tenant data are metered and require billing setup

Agent 365 is not the gate that determines whether a user can invoke a shared agent. That depends on Copilot / Copilot Chat / Teams / SharePoint / Copilot Studio access and metering rules.

### Agent 365 Entitlement is Per-User

Microsoft's licensing FAQ says Agent 365 is **per user**, not per agent, and is tied to the user associated with the agent use case.

One shared agent can continue to be shared. Agent 365 entitlement attaches to the users and scenarios you license. Agent 365 is not a per-agent runtime license that forces every end user of a shared agent into the paid entitlement.

---

## 5. Table 1: Licensed Agent 365 User vs. Unlicensed User on the Same Shared Agent

> **Important note:** cells marked **"not yet documented"** mean Microsoft's public documentation does not yet explicitly answer that question in the sources reviewed. It does **not** mean the platform lacks the capability — these are documentation gaps, not product gaps.

| Dimension | Licensed Agent 365 User | Unlicensed User | What Microsoft Officially Documents |
|---|---|---|---|
| **Does the agent itself change?** | No. The agent does not become a "premium agent." | Same. The agent object does not change because only some users are Agent 365-licensed. | Agent 365 is the control plane; agents do not require their own licenses. |
| **Can the user still use the shared agent?** | Yes, subject to the underlying channel/license path. | Also subject to the underlying channel/license path. | Copilot Chat and Microsoft 365 Copilot docs govern user access and metering, not Agent 365 alone. |
| **Agent 365 entitlement** | Yes, this user is within the per-user Agent 365 license scope. | No, this user is not within the per-user Agent 365 license scope. | Agent 365 is licensed per user, not per agent. |
| **Microsoft 365 Copilot zero-rated agent usage** | If the same user also has Microsoft 365 Copilot, certain usage in Copilot Chat / Teams / SharePoint is zero-rated. | Not unless that user also has Microsoft 365 Copilot. | Zero-rated usage is tied to the Microsoft 365 Copilot user license, not Agent 365. |
| **Copilot Chat no-cost vs. metered behavior** | Depends on whether the agent is declarative/public-web only or accesses tenant data. | Same dependency. | Copilot Chat users can use some agents at no extra cost; tenant-data / metered scenarios require billing setup. |
| **Observability / telemetry in Agent 365 dashboards** | Centralized registry, adoption/activity/health, and role-specific oversight are documented. | **Not yet documented:** whether shared-agent interaction telemetry is partitioned by licensed vs. unlicensed end-user interactions is not yet stated in public sources. | Centralized registry and role-specific oversight are documented; mixed-user telemetry scope is not explicitly addressed. |
| **Security / compliance controls** | Agent 365 + Entra + Purview + Defender are documented for managed agents and agents acting on behalf of users. | **Not yet documented:** how end-user entitlement boundaries apply for the same shared agent; core platform controls are described at the agent/tenant/platform level. | Entra risk-based controls, Purview DLP/information protection, and Defender protections are documented for agents and Copilot/agent workloads broadly. |
| **Visibility risk in a mixed user population** | Lower entitlement ambiguity for licensed users. | **Documentation gap**, not necessarily a platform gap. | Public docs do not yet provide a mixed-user shared-agent observability matrix. |

---

## 6. Table 2: Tenant-Level Features vs. User-Level Licensed Features

| Scope | Feature / Capability | What Microsoft Officially Documents |
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

## 7. What Changes — and What Doesn't — When You Add Agent 365

### What Changes

**1. Your organization gets a centralized control plane.**

You get the Agent 365 registry with unified inventory, lifecycle, role-specific oversight, and integration with Entra/Purview/Defender controls for the managed agent environment.

**2. Licensed users are within Agent 365 commercial entitlement.**

Because Agent 365 is per-user, the users you license are the ones whose agent scenarios are clearly within that entitlement model.

**3. Security and governance posture becomes more explicit around agents.**

Agent identity, least privilege boundaries, DLP/information protection, and threat detection/protection are all documented for managed agents and agents acting on behalf of users.

### What Does Not Change

**1. The agent is still built and run where it was built and run.**

If it is a Copilot Studio agent, Copilot Studio remains the builder/runtime/billing engine. If it is a Foundry agent, Foundry remains the runtime. Agent 365 does not replace those services.

**2. The agent does not need its own Agent 365 license.**

Microsoft's official licensing FAQ explicitly states agents do not require their own licenses.

**3. Runtime consumption mechanics remain in place.**

Copilot Studio still uses Copilot Credits / PAYG / prepaid models for the relevant scenarios, and Copilot Chat metered agent scenarios still require billing configuration where applicable.

**4. Base data access rules do not become looser.**

Access remains bounded by Entra, Purview, and least-privilege controls. Agent 365 does not let agents or users bypass those controls.

---

## 8. Governance, Security, Observability, and Where Documentation Has Gaps

### What Microsoft Clearly Documents

- Centralized registry and role-specific oversight in Agent 365
- Identity and lifecycle control via Entra Agent ID and sponsorship/blueprints
- Purview DLP, information protection, and oversharing controls for Copilot and agents
- Defender threat detection / real-time protection / "shadow AI" expansion in preview announcements

### Where Documentation Has Not Yet Caught Up

Microsoft has not published an article that explicitly addresses this scenario: "If one shared agent is used by 500 people and only 100 of them have Agent 365, what does the Agent 365 portal show?"

That exact telemetry partitioning is not yet covered in public documentation. The org-wide control-plane story is well documented; the end-user entitlement partitioning for mixed shared-agent scenarios is not.

### How to Read the Current State

**Enforcement and visibility are not the same thing.** Microsoft documents many controls as platform/tenant/agent-estate controls (identity, DLP, access control, lifecycle, threat protection), while licensing is per-user. That means:

- **Enforcement / guardrails** = often agent/tenant/platform scoped
- **Commercial entitlement** = per-user
- **Observability scope in mixed shared-agent scenarios** = not yet explicitly documented

---

## 9. What's GA vs. What's Still Expanding

### Generally Available (as of May 1, 2026)

- **Microsoft Agent 365 GA date:** May 1, 2026, commercial, per-user basis
- **Official pricing:** $15/user/month standalone, or included in Microsoft 365 E7
- **Core positioning:** observe, govern, and secure agents across the organization

### In Preview / Expanding

- Observability/governance/security for agents operating **independently with their own credentials and permissions**
- Discovery of agents and **shadow AI** using Defender and Intune for local/cloud agents
- **Windows 365 for Agents** and expanded SaaS ecosystem coverage

The identity architecture for autonomous/own-access agents is already visible in Entra Agent ID documentation, but the full commercial/control-plane story for independently credentialed agents is still evolving. That is the honest way to describe the current state.

---

## 10. Key Explanations

### 30-Second Executive Summary

**Microsoft Agent 365 is Microsoft's control plane for AI agents.** It is the layer IT and security use to see, govern, and secure agents across the company. It is **not** the tool that builds agents and it is **not** the runtime meter. Those remain in products like Microsoft 365 agents, Copilot Studio, and Foundry. Commercially, Agent 365 is **licensed per user, not per agent.**

### For IT Directors and Architects

Think in **three planes**: **build**, **run**, and **govern**. You build agents in Copilot Studio or Foundry (or Microsoft 365 agent tooling), they run in Microsoft 365 channels or Foundry runtime, and **Agent 365** is the cross-estate governance/security/observability plane over that fleet. The management plane is centralized, but the **license is assigned per user**, not to the agent object itself.

### On the Mixed-Licensing Question

Agent 365 is **not** an all-or-nothing per-agent "premium switch." It is a **tenant-wide management/control plane** with a **per-user licensing model**. A shared agent can still be shared by users with and without Agent 365 licenses. What Microsoft has not yet spelled out clearly is the exact telemetry/visibility partitioning for one shared agent used by both licensed and unlicensed users — and it is worth being direct about that gap rather than guessing.

---

## 11. Summary: One Shared Agent, Mixed User Population

### What We Know

- **The agent itself does not change.** Agent 365 is documented as the control plane, not the runtime identity of the agent artifact.
- **Licensed users** are clearly within Agent 365's commercial entitlement model.
- **Unlicensed users** may still be able to use the shared agent if their underlying Copilot/Copilot Chat/channel rights and metering path allow it. Agent 365 is not the runtime gate for that shared agent.
- **The open question** is how Microsoft scopes premium telemetry/observability for mixed-user usage of that same shared agent. Public documentation does not yet provide an explicit matrix for that case.

### The Bottom Line

**Agent 365 is tenant-wide as a management/control plane, but user-based as a license.** It is not a per-agent premium switch, and Microsoft has not yet publicly documented the exact observability partitioning for mixed licensed/unlicensed usage of a shared agent.

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
