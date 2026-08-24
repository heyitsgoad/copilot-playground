# Copilot for Executive Admins

## What This Is

This is the pack I hand to executive assistants and admin professionals after a live working session. It is grouped by the moment you would actually reach for it. The messy thread your executive forwarded with "set this up." The draft that has been sitting in your drafts since yesterday. The trip that lives in six tabs and three confirmation emails. The meeting you missed. The file you cannot find.

The method is three steps. Point it, name the shape, keep the judgment. Everything below is just that method applied to a different Tuesday.

> [!TIP]
> Replace anything in `[brackets]` with your own details before you run it. Names, dates, mailboxes, thread titles. The more specific you are, the less you have to fix afterward.

> [!NOTE]
> Copilot can only work with what it can see. When a prompt refers to a thread, a file, or a meeting, type `/` and point at it. Otherwise Copilot guesses, and you will spend more time correcting it than you saved.

---

## The Method, in Three Steps

- **Point it.** Type `/` to aim Copilot at a file, a thread, or a meeting.
- **Name the shape.** Ask for an agenda, a brief, a checklist. Not just a summary.
- **Keep the judgment.** You edit, you decide, you send.

---

## The Four Ingredients of a Prompt That Works

Most prompts that disappoint people are missing two of these.

| Ingredient | The question it answers | What good looks like |
| --- | --- | --- |
| **Goal** | What do you want back? | Name the artifact. An agenda. A brief. A follow up email. Not "help me with this." |
| **Context** | Why do you need it? | Who is in the room, what is at stake, what your executive cares about. Everybody skips this one, and it is the one you are best at. |
| **Source** | Where should it look? | Type `/` and point at the thread, the file, the meeting. Otherwise it guesses. |
| **Expectations** | How should it come back? | Format, length, tone. Time boxes. Bullets. Under 200 words. |

### All four in one prompt

```
Give me a meeting subject and a 45 minute agenda [GOAL] for tomorrow's leadership meeting where staffing is the sticking point [CONTEXT] using /Regional Leadership Sync [SOURCE] with time boxes, and flag the two points where people still disagree [EXPECTATIONS].
```

---

## One Thing to Know Before You Start

Your delegate access is unchanged. You can still read your executive's mail, send on their behalf, and book their calendar exactly as you always have. What changes is where Copilot sits on top of it. The Summarize and Draft buttons appear in your own mailbox, not theirs. Inside their mailbox, use the Copilot Chat pane and name the mailbox in your prompt.

### Working inside your executive's mailbox, name the mailbox

```
Summarize the recent emails in [exec@yourcompany.com] mailbox and tell me what needs a reply today.
```

---

## 1. The Agenda from the Messy Thread

For when your executive forwards a long thread and says "set this up."

### The agenda

```
Read /[thread name] and give me a meeting subject and a 45 minute agenda with time boxes. Flag the two points where people still disagree.
```

### The pre-read

```
From that same thread, tell me what each attendee needs to decide, and list anything that is still unanswered. Keep it to one screen.
```

### The attendee check

```
Based on this thread, who actually needs to be in the room and who only needs the notes?
```

> [!TIP]
> When Copilot cannot reach the content, paste the thread text straight into Copilot Chat and ask the same question. The prompt does not change. Only the source does.

---

## 2. The Draft You Did Not Want to Write

For the email that has been sitting in your drafts since yesterday.

### The brain dump, start here

```
Here are my rough notes. Turn them into a short, warm, clear email to our [team name]. Keep it under 200 words and put the dates in a list.
[paste your messy notes, bullets and fragments are fine]
```

### The retone

```
Rewrite this so it is direct but not cold. It is going to a VP who is short on time and will read it on a phone.
```

### The hard one

```
I need to tell a group that a deadline moved and it was not their fault. Draft it so it is honest, takes responsibility, and does not sound defensive.
```

### The check, before you send

```
Read this draft and tell me how it will land with someone who is already frustrated. What would you change?
```

---

## 3. The One Page Trip Brief

For the trip that lives in six tabs and three confirmation emails.

### The one page brief

```
Build a one page trip brief for [executive] going to [city] on [dates]. Flights, hotel, ground transport, meetings, and time zone notes. Day by day, and it has to fit on one screen.
```

### The open questions

```
Looking at this itinerary, what is still unconfirmed or missing? Give me a numbered list of questions I can send in a single message.
```

### The checklist

```
Give me a pre-trip checklist for this itinerary, ordered by what has to happen first and what has a deadline.
```

### Pull the planning chat together

```
Summarize the planning conversation in /[Teams chat name], list what was agreed, and tell me what is still open.
```

---

## 4. Catch Up on the Meeting You Missed

Works on Teams meeting recaps, Teams chats, and long Outlook threads.

### The catch up

```
Summarize this meeting. What was decided, what is still open, and what involves [executive name]?
```

### Just my part

```
Did anything in this meeting create a task for [executive name] or for me? Give me only those, with who owns each one.
```

### The follow up

```
Draft a follow up email with the decisions and the action items, with an owner and a due date on each one. Keep it short enough to read on a phone.
```

> [!TIP]
> Same move in Outlook. Open the long thread, use Summary by Copilot at the top, then ask: what does [executive name] actually need to do here?

---

## 5. Find Anything

Describe the thing instead of naming it. Vague is fine. Vague is better.

### Find the file

```
Find the deck about [topic] that [person] shared, probably in the last few months. I do not remember what it was called.
```

### Find the decision

```
What did we decide about [topic]? Show me where that decision was made and who was part of it.
```

### Find the site

```
Locate the SharePoint site for [team or project] and tell me what is actually on it.
```

### Find the owner

```
Who owns [process or document], and when did they last update it?
```

---

## Five More That Did Not Fit in the Hour

### The morning sweep

```
What came in overnight that needs [executive name] before noon? Group it by what needs a decision, what needs a reply, and what is just information.
```

### The person prep

```
I have a meeting with [name] tomorrow. What have we exchanged recently and what is still open between us?
```

### The hidden ask

```
Read this thread and tell me if anyone asked us for something that has not been answered yet.
```

### The document shrink

```
Summarize /[document name] into the five things [executive name] needs to know before walking into the room.
```

### The week ahead

```
Look at my calendar for next week and tell me which meetings still have no agenda and no pre-read.
```

---

## One Honest Ask

Pick one move and run it this week. Not five. One. Then tell whoever is leading the rollout at your company whether it actually worked, and what you had to fix afterward. That feedback is what makes the next round of this better for everyone, and it is the part only you can provide.

---

[Back to the Prompt Playground](../README.md#prompt-playground)
