# Executive Assistant Prompt Pack

## What This Is

This is the set of prompts I hand to executive assistants and admin professionals who want Copilot handling the parts of the job that quietly eat the whole day. Inbox triage, calendar math across time zones, meeting minutes, deck outlines, vendor contracts, and event logistics.

None of these are clever. That is the point. They are the same asks you would give a sharp new hire, written specifically enough that Copilot can actually act on them.

> [!TIP]
> Swap anything in `[brackets]` for your own details before you run it. Names, dates, cities, vendors, headcount. The more specific you are, the less you have to fix afterward.

> [!NOTE]
> Copilot can only work with what it can see. If a prompt refers to a meeting, thread, or document, open it or attach it first so Copilot has the source instead of guessing.

---

## Inbox and Email

The inbox is where most assistants lose the morning. These get you to the short list.

### Catch up after time away

```
Summarize my unread email from the last [3] days into a prioritized list. Put anything with a deadline or that needs a decision at the top, anything needing a reply from me next, and group the FYI updates at the bottom. Tell me who is waiting on us and how long they have been waiting.
```

### Draft a reply in your executive's voice

```
Draft a reply to this email as [Executive Name]. Match how they normally write: [brief, warm, no small talk]. Cover [point one], [point two], and [point three]. Leave a blank line at the bottom for anything they want to add themselves.
```

### Project delay update

```
Draft an update to the [Project Name] team from [Executive Name]. We are [two] days behind schedule. Keep it direct but not heavy-handed, focused on the fix rather than the miss, and ask each team lead to send back a three-point recovery plan by end of day [Friday]. Under 200 words.
```

### Find what you owe people

```
Pull every commitment I made over email this week that has not been closed out yet. Show who I promised it to, what I promised, and when it was due.
```

---

## Calendar and Scheduling

Calendar work is arithmetic plus politics. Copilot can do the arithmetic.

### Three time zones, no bad meetings

```
Find the three best times to hold a [60]-minute meeting for attendees in [Tokyo], [London], and [New York]. Nothing before 9 AM or after 6 PM in anyone's local time. Show each option in all three time zones and tell me which one is the least painful overall and why.
```

### Clean up next week

```
Look at [Executive Name]'s calendar for [next week] and find every conflict, every back-to-back stretch with no gap, and anything double-booked. For each one, tell me what to move and give me two alternate times that already work for the other attendees.
```

### Protect a travel week

```
[Executive Name] is traveling to [city] on [dates]. Review their calendar for those days and tell me what has to move, what can stay virtual, and what I should block for travel and recovery. Give me the list of people I need to email about a change.
```

---

## Meetings and Minutes

Three different asks, so use the one that matches who is reading it.

### One-paragraph readout for the person who missed it

```
Write a one-paragraph summary of this meeting for [Executive Name], who was not there. Lead with what was decided and what happens next. Skip the discussion detail unless it changes a decision.
```

### Formal minutes from a recording or transcript

```
Turn this transcript into formal minutes with these sections: Attendees, Agenda, Discussion Summary, Decisions, Action Items, and Next Steps. Put the action items in a table with owner and due date. Keep the language concise and professional. If an owner or deadline was never actually stated, mark it TBC instead of guessing.
```

### Action items, sorted by person

```
Read this meeting transcript and pull out every statement that implies a task, a deadline, or a follow-up. Organize it by person in a table with the action, the owner, and the due date. This is going into the recap email, so keep each line short enough to scan.
```

> [!TIP]
> The TBC instruction in the minutes prompt matters more than it looks. Without it, Copilot will invent a plausible owner or a due date that nobody agreed to, and you will not catch it until someone misses it.

---

## Documents and Decks

### Report into a five-slide outline

```
Turn this report into a five-slide outline for [Executive Name] to present to [audience]. One key message per slide, three supporting points maximum, and tell me what visual would work on each. Flag any number in the report that I should verify before it goes on a slide.
```

### Vendor contract review

```
Review this contract from [Vendor Name]. Pull out anything about automatic renewal, notice periods, early termination fees, and price increases after year one. Then give me five questions to send to legal before we sign. I am not a lawyer, so explain any term that has a specific legal meaning in plain language.
```

### Pre-meeting brief

```
Build a one-page brief for [Executive Name] ahead of the [meeting name] on [date]. Cover who is attending and their role, what was decided last time, what is still open, and the three questions they are most likely to be asked.
```

---

## Research and Prep

### Competitive snapshot before a pitch

```
Put together a short comparison of [Competitor A] and [Competitor B]. Cover how they have performed over the last 12 months, how they describe their own mission and strategy, and three places they look weak. Keep it to one page and cite where each point came from so I can verify it before it reaches [Executive Name].
```

> [!IMPORTANT]
> Always ask for sources on external research. If Copilot cannot show you where a claim came from, do not put it in front of an executive.

---

## Events and Logistics

### Catering that actually covers everyone

```
Give me three catering options for a [25]-person team lunch in three different cuisines. For each one, list the main dish plus a vegetarian, vegan, and gluten-free equivalent that is a real meal and not just a side salad. Include an estimated cost per person and note anything that travels badly or has to be served hot.
```

### Run of show for an offsite

```
Build a run of show for a [half-day] offsite for [25] people on [date]. Include timing for arrival, sessions, breaks, and lunch, plus who owns each block. Add a column for what I need to have ready in advance for each item.
```

---

## Three Habits That Make These Work Better

- **Give it the source.** Copilot is only as good as what you point it at. Attach the file, open the thread, reference the meeting by name. A vague prompt against no source is where bad output comes from.
- **Say who is reading it.** "For my executive" and "for the board" produce very different drafts. Naming the audience is the cheapest quality upgrade in this whole pack.
- **Never send the first draft.** You know the voice, the history, and the politics in the room. Copilot does not. It gets you to 80 percent in seconds, and the last 20 percent is still the job.

---

*Adapted and expanded from a LinkedIn article on everyday Copilot prompts for administrative professionals. The prompts here have been rewritten and added to.*

[Back to the Prompt Playground](../README.md#prompt-playground)
