# Getting Started with Copilot Governance

![Webinar main](assets/copilot%20webinar/webinar%20main.png)
This is a hands-on governance series that I built with a few of my SEs. It gives you a practical framework for deploying Microsoft 365 Copilot responsibly at scale.

The content walks through end-to-end controls in the M365 Admin Center, Copilot Studio, Power Platform, Microsoft Purview, and SharePoint Advanced Management. It focuses on agent governance, data protection, oversharing mitigation, cost management, and the operational guardrails IT teams actually use.

It’s based on real customer questions and real deployments, not theory.

**Commit: 4 hours**

---

- **Session 1: Copilot and Agent Governance Foundations in the M365 Admin Center**  
  Deployment approach, the Copilot Control System, access and billing controls, and how to highlight or restrict agents.  
  [Read the session recap](https://techcommunity.microsoft.com/blog/healthcareandlifesciencesblog/webinar-copilot-governance-session-1-deployment-copilot-control-system-and-agent/4461801)

- **Session 2: Copilot Studio + Power Platform Governance**  
  Managed Environments, environment routing, DLP strategy, connector risk controls, and cost management for agents.  
  [Read the session recap](https://techcommunity.microsoft.com/blog/healthcareandlifesciencesblog/webinar--session-2-mastering-copilot-governance-with-copilot-studio--power-platf/4463239)

- **Session 3: Purview for M365 + Agents**  
  Sensitivity labels, DLP, insider risk, audit/eDiscovery, and how labeling and oversharing shape what Copilot can surface.  
  [Read the session recap](https://techcommunity.microsoft.com/blog/healthcareandlifesciencesblog/webinar--session-3-mastering-copilot-governance-purview-for-microsoft-365--agent/4464860)

- **Session 4: SharePoint Advanced Management (SAM) for Content Signals**  
  Oversharing baselines, lifecycle cleanup, access reviews, RAC/RCD, and making Copilot “see” the right content.  
  [Read the session recap](https://techcommunity.microsoft.com/blog/healthcareandlifesciencesblog/mastering-copilot-content-governance-with-sharepoint-advance-management---sessio/4467427)

---

## Session 1: The Admin‑Center Foundations

### Outcomes to aim for

1. **Phased rollout plan** with ownership and change management from day one.  
2. **Copilot Control System** set for who can build, which agents are pinned, and how billing is scoped.  
3. **Guardrails** for web search, external connectors, and business dictionaries.  

### Checklist

- Scope agent creation to security groups. Pin key agents. Track ownerless agents.  
- Align pay‑as‑you‑go by department or group, and limit high‑risk third‑party connectors.  
- Plan Graph Connectors (e.g., ServiceNow) with governance in mind.  

**Resources**

- [Watch the recording](https://www.youtube.com/watch?v=Ie7ADxONHtw)  
- [Blog reference](https://techcommunity.microsoft.com/blog/healthcareandlifesciencesblog/webinar-copilot-governance-session-1-deployment-copilot-control-system-and-agent/4461801)  

---

## Session 2: Copilot Studio + Power Platform Governance

### Core decisions

- **Managed Environments** on, always. That unlocks advanced policy, monitoring, and routing.  
- **Environment strategy** with dev/UAT/prod and dedicated agent environments, plus **environment routing** to stop sprawl.  
- **DLP tiers** (tenant baseline + layered per environment), role‑based access, risky‑connector notifications.  
- **Cost model**: prepaid message packs vs PAYG, allocations by tenant/environment/agent. Use the estimator before you scale.

### Top tips

- Refresh DLP as new connectors and features land.  
- Use **Copilot Studio Authors** to onboard makers cleanly.  
- Wire up **App Insights** for deeper diagnostics.  

**Resources**

- [Watch the recording](https://www.youtube.com/watch?v=KSkJqHnO_TE)  
- [Blog reference](https://techcommunity.microsoft.com/blog/healthcareandlifesciencesblog/webinar--session-2-mastering-copilot-governance-with-copilot-studio--power-platf/4463239)  

---

## Session 3: Purview for Information Protection, Audit, and Risk

### How protection maps to Copilot

- **Sensitivity labels**: Copilot respects access controls. Blended outputs inherit the **highest** sensitivity from sources.  
- **DLP & Insider Risk**: Block processing for specific labels or projects, monitor exfiltration, and apply adaptive protection.  
- **Audit & eDiscovery**: Track Copilot interactions and include them in investigations.  

### Operating model

- Start new policies in **audit‑only** to tune before enforcement.  
- Build **custom label templates** with the business, not just IT.  
- Clarify **E3 vs E5** expectations: advanced DSPM/auto‑label in E5, more manual effort in E3.  

**Resources**

- [Watch the recording](https://www.youtube.com/watch?v=7dgDo5cKeYY)  
- [Blog reference](https://techcommunity.microsoft.com/blog/healthcareandlifesciencesblog/webinar--session-3-mastering-copilot-governance-purview-for-microsoft-365--agent/4464860)  

---

## Session 4: SharePoint Advanced Management (SAM) for Better Signals

### Goal

Tighten sharing, clean up stale sites, and reduce broad access so Copilot sees the right content.

### 5 moves that matter

1. **Review sharing defaults** and remove “Everyone except external users” when appropriate. Require owner approval where possible.  
2. **Lifecycle cleanup** with Inactive Site Policy. Archive or delete to cut risk and noise. Archived sites are cheaper and invisible to Copilot.  
3. **Oversharing Baseline (DAG)** across all sites, not just recent activity. Export, sort by sensitivity and reach, then remediate.  
4. **Delegate access reviews** to site owners. Track progress in admin.  
5. **Short‑term controls**:  
   - **RAC** to lock a site to approved groups  
   - **RCD** to hide a site from Copilot and cross‑site search without breaking permissions  

### Bonus

Enforce **Site Ownership Policy** and consider **Blocked Download** on sensitive containers. Combine SAM with Purview labels for better reporting.

**Resources**

- [Watch the recording](https://www.youtube.com/watch?v=VxTXvDeIGvk)  
- [Blog reference](https://techcommunity.microsoft.com/blog/healthcareandlifesciencesblog/mastering-copilot-content-governance-with-sharepoint-advance-management---sessio/4467427)  

---

## Put It All Together: The Governance Stack

| Layer                   | What you decide                                                     | Tools you use                                                    |
|-------------------------|---------------------------------------------------------------------|------------------------------------------------------------------|
| **Access & Controls**   | Who can build agents, which agents are pinned, how you bill and monitor | M365 Admin Center, Copilot Control System                    |
| **Agent Platform**      | Environments, routing, DLP tiers, connector governance, cost model  | Copilot Studio, Power Platform governance (Managed Environments, DLP, routing) |
| **Information Protection** | Labels, DLP, insider risk, audit/eDiscovery                    | Purview IP, DLP, Insider Risk, Audit, eDiscovery               |
| **Content Signals**     | Sharing defaults, lifecycle, access reviews, RAC/RCD               | SharePoint Advanced Management (SAM)                           |

---

## Quick Start for Execs

- **Week 1–2**: Approve the **environment strategy** and **Managed Environments**. Turn on routing. Set baseline DLP.  
- **Week 3–4**: Run **DAG oversharing** and **inactive site** reports, kick off access reviews, apply RAC/RCD on hot spots.  
- **Weeks 5–6**: Align labels and DLP with business terms, enable audit‑only rules, then enforce. Wire up reporting for execs.  
- **Ongoing**: Pin approved agents, monitor ownerless agents, and review consumption and connector usage monthly.  

---

## Resources

- [Copilot Governance: A Practical Guide From Our 4-Part Webinar Series](https://techcommunity.microsoft.com/blog/healthcareandlifesciencesblog/copilot-governance-a-practical-guide-from-our-4%E2%80%91part-webinar-series/4469033), the written summary of all four sessions in one place  
- [Copilot Success Kit](https://adoption.microsoft.com/en-us/copilot/success-kit/)  
- [Implementation Guide](https://aka.ms/Copilot/ImplementationSummaryGuide)  
- [Technical Readiness Guide](https://aka.ms/Copilot/TechnicalReadinessGuide)  
- [User Enablement Guide](https://aka.ms/Copilot/UserEnablementGuide)  

---

## YouTube Video Playlist

[View all our sessions in a playlist](https://www.youtube.com/playlist?list=PLdkhFJc5w6-F-J9Os8IzyGy969USAMSIx)

![Copilot governance](assets/copilot%20webinar/copilot%20governance.png)

---

[Back to the Education Playground](../README.md#education-playground)
