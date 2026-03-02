![image alt](https://github.com/heyitsgoad/copilot-playground/blob/c6e79f9a6ad0ce68afdd74e717b22076c078d24d/education%20playground/assets/copilot%20webinar/Agent%20Mode/Claude%20in%20Copilot%206.png)


There’s been a lot of attention lately on Claude and how strong it is with Excel and structured data.
What most people don’t realize is that if you’re using Microsoft 365 Copilot, you already have access to that level of capability inside Excel.

This repo supports a hands on rebuild of the demo from the video. You can watch it end to end, or download the files and follow along step by step using the same prompts I use.

Watch the full video on YouTube:
https://youtu.be/zkaRUDSDBwk?si=6EGZujNUsCmeYfIl

## How to follow along (recommended)
If you want to rebuild this yourself, use the steps below in order.
### 1) Download the mock RAW data
This demo uses synthetic data generated for education and walkthrough purposes.
File:
PlatteCountyMO_Q2_2025_ParamedicOvertime_RAW.xlsx
What’s inside (so it feels realistic):
- Overtime_Raw (3,416 rows): Shift level records with role, station, shift, overtime hours, overtime reason, pay details, call volume, and staffing gap flags
- Employee_Roster (74 employees): Role mix, FTE, station assignment, tenure band, base rates
- Call_Volume_Daily (91 days): Total calls, high acuity calls, transports, mutual aid, weather and event flags
- Staffing_Daily (182 rows): Day/night planned vs actual headcount, sick calls, vacancies, staffing gaps
- OT_Budget: Monthly overtime budget targets (hours and cost)
- Quick_Aggregates: A basic aggregation table you can use as a sanity check
Design choices baked into the data:
- Seasonality with a clear May surge in call volume and staffing gaps
- Mix of overtime reasons (holdover, backfill, sick coverage, event standby, weather surge)
- A small group of employees with repeated high OT late in May (creates risk and discussion)
- Night differential and overtime multipliers included
### 2) Enable Agent Mode in Excel
Agent Mode is required for the analyst prompts below.
1. Open the workbook in Excel for Desktop
2. Open Copilot
- You may see Copilot in the ribbon, or as the floating Copilot icon in the bottom right (both are fine)
3. Select Edit with Copilot
4. Choose Agent Mode
- This enables deeper reasoning, multi step analysis, and native Excel artifact creation
5. If available, confirm Claude is enabled under model selection
- If you don’t see Claude, your IT admin likely hasn’t enabled Anthropic yet
Once Agent Mode is on, you’re ready to run the prompts.
## 3) Analyst Prompt Pack (Agent Mode)
These prompts turn RAW data into dashboards, insights, and executive artifacts. Run them in order.
### Prompt 0: Prepare the data model (run first)
Prompt:
Create a clean reporting model from the existing sheets. Convert Overtime_Raw, Call_Volume_Daily, Staffing_Daily, and OT_Budget into Excel Tables with clear names. Ensure Date columns are typed as dates. Add Month (Apr, May, Jun) and WeekStart (Monday) columns to Overtime_Raw. Create relationships using Date between Overtime_Raw, Call_Volume_Daily, and Staffing_Daily. Create new sheets named Dashboard and SBAR.
Expected output:
- Tables: tblOvertimeRaw, tblCallsDaily, tblStaffingDaily, tblOTBudget
- New sheets: Dashboard, SBAR
### Prompt 1: Build the executive KPI strip
Prompt:
On the Dashboard sheet, create a KPI strip for Q2 (Apr 1–Jun 30, 2025) showing total overtime hours, total overtime cost, cost vs budget (variance $ and %), hours vs budget (variance hours and %), cost per call, and the top overtime driver by hours. Format it as a clean executive summary.
### Prompt 2: Create the core dashboard visuals
Prompt:
Build an executive dashboard with charts for overtime cost by month (with budget line), overtime hours by week, overtime hours by station, overtime hours by reason (Pareto), and a scatter of total calls vs overtime hours by day highlighting May outliers. Add slicers for Month, Station, Shift, and Role. Keep the layout simple and executive friendly.
### Prompt 3: Find the story (what changed in May?)
Prompt:
Analyze what drove overtime in May compared to April and June. Identify the top 3 drivers and quantify their impact in hours and dollars. Flag operational risks such as concentration, repeated holdovers, or persistent staffing gaps. Add a “May Drivers” section to the Dashboard with bullet insights.
### Prompt 4: Build an SBAR for the CFO
Prompt:
On the SBAR sheet, create a CFO ready SBAR summary covering Situation, Background, Assessment, and Recommendations. Include numbers, risks, and actions grouped by immediate, near term, and structural timeframes. Keep the tone direct and numbers first.
### Prompt 5: VP talking points
Prompt:
Create a “VP Talking Points for CFO” section with five numbered highlights, three likely CFO questions with answers, and two decisions needed with estimated impact. Place it on the Dashboard and link values to the underlying tables.
### Prompt 6: Stress test (what if scenarios)
Prompt:
Create a What If sheet that models staffing and policy changes and shows estimated overtime savings, intervention costs, and net impact. Present results in a clean table and a simple waterfall chart.
## 4) Executive Prompt Pack (after handoff)
Once the workbook is built, the VP should focus on decisions, not analysis.
Example prompts included:
- CFO headline summary
- Risk identification
- Month over month changes
- Decision options with tradeoffs
- Board level speaking points
## Why this demo lands
- The CFO asks a question in plain English
- Analysts use Agent Mode to build native Excel artifacts
- Executives extract decisions, not charts
- ROI shows up as time to answer and quality of decision
Agent Mode isn’t typing formulas.
It’s producing usable Excel workbooks, iterating, and validating until the result is ready.
