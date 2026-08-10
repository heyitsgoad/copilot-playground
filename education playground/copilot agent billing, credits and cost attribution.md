# Copilot Agent Billing: Credits, Cost Attribution, and Who Actually Pays

![Copilot agent billing: who pays, where the charge lands, and how to structure Azure so it lands in the right cost center](assets/copilot%20agent%20billing/banner.png)

> [!IMPORTANT]
> **Read this first: these are my own views.** This is a personal, community resource, and the analysis, opinions, and recommendations in it are my own. I work at Microsoft, but this is **not** an official Microsoft publication, not an official Microsoft position, not pricing guidance, and not an offer or commitment. Where I interpret Microsoft's documentation, draw a conclusion, or recommend an approach, that is my perspective as a practitioner rather than a statement on behalf of Microsoft or my employer.
>
> Every figure is an illustrative planning number from public documentation as of August 4, 2026, and none of it reflects contract or negotiated pricing. Nothing here supersedes the Microsoft Product Terms, your agreement, or the live rate card. Confirm anything you are about to spend money on.

Someone builds an agent. A month later a charge shows up on the Azure bill and it is not clear who caused it or which budget it should hit. That conversation happens at almost every organization rolling out Copilot, and it usually stalls the rollout while finance and IT try to source a number neither of them owns.

This guide answers it. It covers how agent usage is billed across Agent Builder, Copilot Studio, Cowork, and Foundry, what Copilot Credits actually cost, where each billing surface is configured, and how to structure Azure subscriptions and resource groups so consumption lands in the right cost center instead of a shared pool nobody owns.

> [!TIP]
> Open the interactive guide below. It has a decision tool that tells you whether a specific agent will cost you anything before you build it, a credit calculator for quick sanity checks in a meeting, light and dark mode, and a jump nav so a finance lead can read three sections while an admin reads the deep mechanics.

---

## Get the guide

| Deliverable | What it is | Open or download |
|---|---|---|
| **Interactive guide** | The full reference: license model, free vs. metered boundary, credit rate card, the four billing surfaces, Azure cost attribution, purchase options, spend controls, reporting, and rollout checklist. Includes a live decision tool and credit calculator. | [Open in browser](https://heyitsgoad.github.io/copilot-playground/education%20playground/assets/copilot%20agent%20billing/) · [Download HTML](https://github.com/heyitsgoad/copilot-playground/raw/main/education%20playground/assets/copilot%20agent%20billing/index.html) |
| **PDF reference** | The same content as a 48 page printable document, with the glossary and every collapsible section expanded. This is the one to forward to a colleague or attach to a governance review. | [Download PDF](https://github.com/heyitsgoad/copilot-playground/raw/main/education%20playground/assets/copilot%20agent%20billing/Copilot-Agent-Billing-Guide.pdf) |

> [!TIP]
> Ctrl-click (Cmd-click on Mac) any link to open it in a new tab.

---

## The Whole Thing in Seven Lines

1. **Building an agent is free. Running it is what costs.** Authoring is never a billable event.
2. **A paid Microsoft 365 Copilot license is the biggest single factor, but not a simple on/off switch.** It zero-rates ordinary, interactive, employee-facing use. It does not cover autonomous runs, computer use, bring-your-own models, external hosting, or customer-facing scenarios. And an unlicensed user is not automatically charged either: instructions-only and public-web agents are free for everyone.
3. **Nobody is billed personally.** Where cost lands depends on which funding path you are on. Usually an Azure subscription and resource group named in a billing policy, but prepaid capacity packs with a credit policy need no Azure subscription at all.
4. **The currency is Copilot Credits**, about $0.01 each on pay-as-you-go. One user question can trigger several charges at once.
5. **Each surface bills somewhere different.** Agent Builder and Copilot Chat in the Microsoft 365 admin center, Copilot Studio in the Power Platform admin center, Cowork under Copilot > Cost Management, Foundry directly in Azure on Azure meters rather than credits.
6. **The two policy types scope differently.** Microsoft 365 billing policies scope to users and groups. Power Platform billing plans scope to environments. That makes environments your Copilot Studio reporting dimension, so design environments and your cost model together.
7. **Most budgets do not stop anything.** Azure budgets and Microsoft 365 policy budgets alert only. Per-agent credit limits and Cowork spending limits genuinely enforce.

---

## The Economic Shape, in One Paragraph

A paid Microsoft 365 Copilot seat zero-rates ordinary, interactive, employee-facing agent use. You already paid for that when you bought the seat. Metering starts at the edges: unlicensed users reaching into organizational data, autonomous or scheduled runs, computer-use agents, and bring-your-own models. That is the difference between per-seat inclusion and per-interaction consumption. On a purely consumption-priced platform every interaction is a charge. Here the everyday majority is already covered, and the work is keeping usage inside that zero-rated core while putting deliberate controls on the metered edges.

---

## What You Will Learn

- Why "we should buy Copilot Premium licenses" is a request that cannot be fulfilled as written, and what to ask for instead
- The four conditions that all have to be true before a paid license makes agent usage free, and the seven scenarios where it does not
- The exact line between free and metered for a user on included Copilot Chat, including the one data type you cannot buy your way into
- What a Copilot Credit costs, the full published rate card, and why credits are not tokens
- Where each of the four billing surfaces is configured, and the scoping difference that breaks most chargeback models
- What a resource group actually is in billing terms, and the assumption that derails cost models
- All three ways to buy credits, including the commercial details worth confirming with your account team
- Whether agent identity (Entra Agent ID) has anything to do with billing, and why the answer is no
- Whether you can run more than one billing policy on the same service, and the All-users rule that makes it look like you cannot
- How the four different policy objects (billing policies, credit policies, Cowork spending policies, Power Platform billing plans) actually differ
- Which spend controls genuinely enforce and which only send email
- How to get Copilot usage into Power BI, and the one report that does not exist
- How to align Azure subscriptions and resource groups to business units without over-engineering it

---

## Who This Is For

- **IT and platform owners** who have to turn billing on, scope it, and explain it
- **Finance and FinOps partners** who need to know where the charge lands and how to allocate it
- **Anyone who has been asked "what will this agent cost us"** and did not have a defensible answer
- **Regulated and healthcare environments** where the cost model and the compliance boundary both have to hold up

---

## What Makes This One Different

Most billing explanations round off the hard parts. This one works through them. Every figure was checked against live Microsoft documentation before publication, and the guide cites its sources so you can verify anything before you spend against it. Where Microsoft's own documentation contradicts itself, the guide says so and tells you to test it in your tenant rather than picking the answer that sounds cleaner. Three of those are called out explicitly:

- Whether pay-as-you-go actually unlocks SharePoint and OneDrive knowledge in Agent Builder
- Whether AI Builder tools are zero-rated for licensed users
- Whether Copilot Studio is named in-scope for HIPAA

It also clears up several points that are easy to get wrong: that a paid seat makes all agent usage free, that an unlicensed user always costs you money, that Azure budgets stop spend, that the Copilot Dashboard is a Power BI report you can customize, that giving an agent an Entra Agent ID is how you bill it, and that credits and tokens are the same thing.

> [!NOTE]
> There is a dated item in here worth acting on. **Seeded AI Builder credits are removed on November 1, 2026**, and they are a different currency from Copilot Credits with no automatic conversion. If anyone in your organization is planning against a credit pool, confirm which currency it actually is before you build a budget on it.

---

## Sources

Section 15 of the guide lists the primary references behind it. Version 1.4 adds a plain-language glossary of the sixteen terms that carry the guide, hover definitions on those terms throughout, a plain-terms summary at the top of every heavy section, and splits the old section 05 into separate sections for the four billing surfaces and for splitting cost across teams. Rates, product names, and admin surfaces change often, so treat every figure as a planning number and confirm against the live rate card and your own agreement before committing budget. Version 1.4, current as of August 4, 2026, next review due by November 4, 2026.

---

## Related

- [Copilot Licensing and Deployment: Who Gets What](https://github.com/heyitsgoad/copilot-playground/blob/main/education%20playground/copilot%20licensing%20and%20deployment%2C%20who%20gets%20what.md) for the role-by-role view of who should get a paid seat in the first place
- [Microsoft Agent 365: Licensing, Architecture, and How It Fits Into Your AI Strategy](https://github.com/heyitsgoad/copilot-playground/blob/main/education%20playground/microsoft%20agent%20365%20licensing%20architecture%20and%20how%20it%20fits%20into%20your%20ai%20strategy.md) for the governance and identity layer above the billing layer
- [Getting Started Guide for Copilot Governance](https://github.com/heyitsgoad/copilot-playground/blob/main/education%20playground/copilot%20governance%20getting%20started.md) for the broader admin and compliance picture
- [Right-Sizing Cowork: Who Actually Needs It](https://github.com/heyitsgoad/copilot-playground/blob/main/education%20playground/right-sizing%20cowork%20who%20actually%20needs%20it.md) for scoping Cowork before you turn the meter on

---

[Back to the Education Playground](../README.md#education-playground)
