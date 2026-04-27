# Daily Executive Field Readout

## What This Is

A fully automated daily briefing prompt that runs every weekday at 8:00 AM and reviews the past 24 hours across your calendar, email, Teams, and tasks. It surfaces customer commitments, internal follow-ups, pending responses, risks, meeting recaps, inbox highlights, team availability, and field coordination guidance, all in one structured readout.

Each run generates three outputs: an Executive Summary, a PowerPoint briefing saved to your OneDrive, and an HTML presentation for async browser review, all delivered to your inbox automatically.

> [!TIP]
> Swap in your own account list, customer numbers, projects, and OneDrive folder path before running.

---

## Prompt

Run every Monday through Friday at 8:00 AM

Review the past 24 hours across:

- My Outlook calendar
- Emails
- Microsoft Teams chats
- To Do / Planner tasks
- Account-related communications

Focus on customer-facing activity tied to healthcare and life sciences accounts, especially: `{replace the below with customer, project, etc}`

| Customer Name | 

Also surface any new customer accounts that appear in communications.

---

### Section 1: Customer Commitments

List anything I committed to delivering externally, including:

- Sending follow-up material
- Scheduling demos or meetings
- Technical validation or architecture support
- Copilot or agent workshops
- Executive briefings

Include: Customer name, contact, commitment made, and what is at stake if missed.

---

### Section 2: Internal Follow-ups

Actions I owe internally to:

- Account Executives
- Cusotmer Success Managers
- Project Managers
- Technical Architects
- Account Team members

Include: What needs to be done, who it impacts, associated account, and upcoming timelines.

---

### Section 3: Pending Responses

Highlight:

- Customer emails awaiting response
- Internal questions tied to customer work
- Teams messages that require follow-up

Call out anything that may affect deal progression, customer trust, workshop readiness, or executive alignment.

---

### Section 4: Risks or Blockers

Identify anything that could:

- Delay delivery
- Stall adoption
- Create licensing confusion
- Impact Copilot rollout
- Damage customer relationship momentum

Note where information is missing or could not be retrieved.

---

### Section 5: Meeting Recap and Today's Priorities

Provide:

- Summary of yesterday's customer-related meetings
- Key decisions or action items
- Overview of today's scheduled meetings
- Any deadlines or due dates requiring attention

Flag any 1:1s, executive briefings, workshops, or MTC sessions that may require preparation.

---

### Section 6: Inbox Review

Highlight urgent, unread, and flagged emails tied to customer work. List any tasks or follow-ups derived from inbox activity.

---

### Section 7: Team Availability Snapshot

Review my immediate account team and collaborators. Identify anyone who is out of office, on PTO or DTO, traveling, in training, or otherwise unavailable today. Call out anyone I may need to cover for or follow up with.

---

### Section 8: Field Coordination Guidance

Based on current activity:

- Who should I connect with today
- What follow-ups should I prioritize
- Any coordination needed across the account team

---

### Section 9: Inspiration Tip of the Day

Provide one short, practical tip related to Copilot usage, AI transformation leadership, agent-based workflow design, executive adoption of AI, or driving change with Microsoft AI solutions. Keep it actionable and relevant to field execution.

---

## Deliverables Generated

**A. Executive Summary**
A concise executive-level summary highlighting top customer commitments, major internal follow-ups, primary deal risks, team availability impacts, and top priorities for the day.

**B. PowerPoint Briefing**
A PowerPoint presentation titled *Daily Executive Field Briefing* saved to OneDrive under:
`Documents → Cowork → Daily Briefings`

Slides include: Executive Summary, Customer Commitments, Internal Follow-ups, Pending Responses, Risks or Blockers, Today's Meetings and Priorities, Team Availability Snapshot, Field Coordination Guidance, and Inspiration Tip of the Day.

**C. HTML Executive Presentation**
An HTML-based executive presentation with the same sections for quick browser-based review, saved to the same Daily Briefings folder.

**D. Email Delivery**
Subject: `Daily Executive Field Readout`
Body includes the Executive Summary and a note that the full PowerPoint and HTML briefing have been saved to OneDrive under `Documents → Cowork → Daily Briefings`.
