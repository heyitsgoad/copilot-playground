# Copilot Agent Billing: Credits, Cost Attribution, and Who Actually Pays

![Copilot agent billing: who pays, where the charge lands, and how to structure Azure so it lands in the right cost center](https://github.com/heyitsgoad/copilot-playground/raw/main/education%20playground/assets/copilot%20agent%20billing/banner.png)

Someone builds an agent. A month later a charge shows up on the Azure bill and nobody can explain who caused it or which budget it should hit. That conversation happens at almost every organization rolling out Copilot, and it usually stalls the rollout while finance and IT argue about a number neither of them can source.

This guide answers it. It covers how agent usage is billed across Agent Builder, Copilot Studio, Cowork, and Foundry, what Copilot Credits actually cost, where each billing surface is configured, and how to structure Azure subscriptions and resource groups so consumption lands in the right cost center instead of a shared pool nobody owns.

> [!TIP]
> Open the interactive guide below. It has a decision tool that tells you whether a specific agent will cost you anything before you build it, a credit calculator for quick sanity checks in a meeting, light and dark mode, and a jump nav so a finance lead can read three sections while an admin reads the deep mechanics.

---

## Get the guide

| Deliverable | What it is | Open or download |
|---|---|---|
| **Interactive guide** | The full reference: license model, free vs. metered boundary, credit rate card, the four billing surfaces, Azure cost attribution, purchase options, spend controls, reporting, and rollout checklist. Includes a live decision tool and credit calculator. | [Open in browser](https://heyitsgoad.github.io/copilot-playground/education%20playground/assets/copilot%20agent%20billing/) · [Download HTML](https://github.com/heyitsgoad/copilot-playground/raw/main/education%20playground/assets/copilot%20agent%20billing/index.html) |
| **PDF reference** | The same content as a 35 page printable document, with every collapsible section expanded. This is the one to forward to a colleague or attach to a governance review. | [Download PDF](https://github.com/heyitsgoad/copilot-playground/raw/main/education%20playground/assets/copilot%20agent%20billing/Copilot-Agent-Billing-Guide.pdf) |

> [!TIP]
> Ctrl-click (Cmd-click on Mac) any link to open it in a new tab.

---

## The Whole Thing in Six Lines

1. **The license of the person using the agent decides whether it meters.** Not the person who built it. Building costs nothing; running costs something.
2. **Nobody is billed personally.** Consumption lands in whatever Azure subscription and resource group an admin named in a billing policy. Departmental cost attribution has to be configured, it does not happen on its own.
3. **The currency is Copilot Credits**, about $0.01 each on pay-as-you-go. One user question can trigger several charges at once.
4. **Each build surface bills somewhere different.** Agent Builder and Copilot Chat in the Microsoft 365 admin center, Copilot Studio in the Power Platform admin center, Cowork under Copilot > Cost Management, Foundry directly in Azure.
5. **The two policy types scope differently.** Microsoft 365 billing policies scope to users and groups. Power Platform billing plans scope to environments. You cannot chargeback Copilot Studio by security group.
6. **Most budgets do not stop anything.** Azure budgets and Microsoft 365 policy budgets alert only. The controls that actually halt spend are per-agent credit limits, Cowork spending limits, and prepaid capacity with no overflow.

---

## What You Will Learn

- Why "we should buy Copilot Premium licenses" is a request no reseller can fulfill, and what to ask for instead
- The four conditions that all have to be true before a paid license makes agent usage free, and the seven scenarios where it does not
- The exact line between free and metered for a user on included Copilot Chat, including the one data type you cannot buy your way into
- What a Copilot Credit costs, the full published rate card, and why credits are not tokens
- Where each of the four billing surfaces is configured, and the scoping difference that breaks most chargeback models
- What a resource group actually is in billing terms, and the misconception that derails cost models
- All three ways to buy credits, including which commercial detail gets misquoted most often
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

Most billing explanations round off the hard parts. This one does the opposite. Where Microsoft's own documentation contradicts itself, the guide says so and tells you to test it in your tenant rather than picking the answer that sounds cleaner. Three of those are called out explicitly:

- Whether pay-as-you-go actually unlocks SharePoint and OneDrive knowledge in Agent Builder
- Whether AI Builder tools are zero-rated for licensed users
- Whether Copilot Studio is named in-scope for HIPAA

It also corrects several things that get repeated confidently in the field and are wrong: that a paid seat makes all agent usage free, that Azure budgets stop spend, that the Copilot Dashboard is a Power BI report you can customize, and that credits and tokens are the same thing.

> [!NOTE]
> There is a dated item in here worth acting on. **Seeded AI Builder credits are removed on November 1, 2026**, and they are a different currency from Copilot Credits with no automatic conversion. If anyone in your organization is planning against a credit pool, confirm which currency it actually is before you build a budget on it.

---

## Sources

Every substantive claim traces to Microsoft documentation, and section 14 of the guide lists all of them. Rates, product names, and admin surfaces change often, so treat the figures as planning numbers and confirm against the live rate card and your own agreement before committing budget. Current as of July 31, 2026.

---

## Related

- [Copilot Licensing and Deployment: Who Gets What](https://github.com/heyitsgoad/copilot-playground/blob/main/education%20playground/copilot%20licensing%20and%20deployment%2C%20who%20gets%20what.md) for the role-by-role view of who should get a paid seat in the first place
- [Microsoft Agent 365: Licensing, Architecture, and How It Fits Into Your AI Strategy](https://github.com/heyitsgoad/copilot-playground/blob/main/education%20playground/microsoft%20agent%20365%20licensing%20architecture%20and%20how%20it%20fits%20into%20your%20ai%20strategy.md) for the governance and identity layer above the billing layer
- [Getting Started Guide for Copilot Governance](https://github.com/heyitsgoad/copilot-playground/blob/main/education%20playground/copilot%20governance%20getting%20started.md) for the broader admin and compliance picture
- [Right-Sizing Cowork: Who Actually Needs It](https://github.com/heyitsgoad/copilot-playground/blob/main/education%20playground/right-sizing%20cowork%20who%20actually%20needs%20it.md) for scoping Cowork before you turn the meter on
