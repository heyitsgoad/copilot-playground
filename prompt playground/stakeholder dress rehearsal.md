# Stakeholder Dress Rehearsal

## What This Is

A pre-send pressure test for anything you're about to put in front of a room. Copilot pulls the last 60 days of your emails, Teams conversations, meeting notes, and documents, then plays three audiences at once: the executive sponsor who has to fund it, the skeptical customer who has to buy it, and the delivery team who has to build it.

You get a reaction map showing what each group supports, questions, or misreads, with the actual work sources behind every reaction. Then it rewrites your message so all three land, capped at 300 words.

Run it before you hit send on a proposal, an announcement, or a recommendation that needs buy-in from people who don't share the same priorities.

> [!TIP]
> Swap the bracketed placeholder for your actual proposal, announcement, or recommendation. Paste your draft message after the prompt so Copilot has something concrete to rewrite. If your three audiences are different, name them, for example a board member, a partner, and a compliance reviewer.

---

## Quick Copy

```
I'm preparing to share [proposal, announcement, or recommendation]. Review the related emails, Teams conversations, meeting notes, and documents from the past 60 days. Simulate how an executive sponsor, a skeptical customer, and the team responsible for delivery would react: identify what each audience will support, question, or misunderstand; cite the work sources behind each reaction; then rewrite my message so it addresses all three perspectives without becoming longer than 300 words.
```

---

## Prompt (Full Breakdown)

### What You're Testing

Name the thing you're about to share.

- `[proposal, announcement, or recommendation]`

Be specific. "The Q3 platform migration proposal" beats "my proposal." The more precise the subject, the better Copilot scopes which threads and documents actually matter.

---

### Sources to Review

The past 60 days of:

| Source | What it surfaces |
|---|---|
| Emails | Stated positions, prior objections, who has already pushed back |
| Teams conversations | The unfiltered version, side concerns, real sentiment |
| Meeting notes | Commitments made, questions left open |
| Documents | Scope, numbers, and detail people will check you against |

> [!NOTE]
> Sixty days is the default because it usually covers one full planning cycle without dragging in stale context. Widen it if the decision has a longer history. Narrow it if the situation changed recently.

---

### The Three Audiences

Copilot simulates each one separately, not as a blended average.

**Executive sponsor**
Cares about outcome, cost, risk, and whether this competes with something else they already funded.

**Skeptical customer**
Cares about whether it solves their problem, what it costs them, and what happens when it doesn't work.

**Delivery team**
Cares about scope, timeline realism, dependencies, and who is actually doing the work.

---

### What Each Reaction Must Include

For every audience, three things:

| Reaction | What it means |
|---|---|
| Support | What they'll agree with immediately and why |
| Question | What they'll push on before committing |
| Misunderstand | Where your wording invites the wrong conclusion |

The misunderstand column is the one people skip. It's usually where the meeting goes sideways.

---

### Cite the Sources

Every reaction has to point back to something real, a specific email, thread, meeting, or document. This is the part that keeps the exercise honest.

If Copilot can't cite a source for a reaction, treat that reaction as a guess and weigh it accordingly.

---

### The Rewrite

The final output is a new version of your message that handles all three perspectives.

- Hard cap at 300 words
- Addressing more audiences without adding length forces real editing
- If it comes back longer, ask for it again at 250

---

### Follow-Up Prompts

- "Which of these three audiences is most likely to block this, and what would change their mind?"
- "Show me the two sentences in my original draft that caused the most misunderstanding."
- "Rewrite it again assuming the executive sponsor reads only the first paragraph."

---

[Back to the Prompt Playground](../README.md#prompt-playground)
