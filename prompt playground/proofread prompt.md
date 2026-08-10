# Proofread

## What This Is

A senior copyediting pass for anything you have written. You paste an excerpt, and Copilot returns each change with the reasoning behind it, grouped under headers, then gives you the clean revised version at the end.

It is built to tighten and clarify without flattening your voice.

> [!TIP]
> Replace `[end state]` in the first line with the kind of writing you want critiqued, for example `technical documentation`, `executive email`, or `landing page copy`. The more specific you are, the sharper the edit.

## Requirements

- Microsoft 365 Copilot (Premium)
- Microsoft 365 Copilot Chat (free)

---

## Quick Copy

```
Act as a senior copywriter with over 20 years of experience writing [end state].

I want you to improve my writing. I'll share an excerpt and your task is to proofread the excerpt and provide recommendations based on the following criteria.

Break down each change and share the corresponding explanation for the edit before sharing the completed revised excerpt. Group these together using Headers for easy readability.

Editing criteria:
- Trim the fat: Each sentence serves a clear purpose without excess words.
- Improve the clarity of my writing so the reader can easily digest my message.
- Look for and correct all misspelled words and grammatical errors.
- Use active voice throughout.
- Where possible, use shorter synonyms of longer words, break up excessively long sentences into short ones, keep paragraphs brief, and use effective transitions.
- Preserve as much of the original tone and style as possible, and do not add any filler content.
- Use an informal yet professional tone: Use contractions and casual phrases while maintaining credibility.

Here is my excerpt:
[insert excerpt]
```

---

## What each instruction is doing

| Instruction | What it controls |
|---|---|
| `senior copywriter with over 20 years of experience` | Sets the bar. You get judgment calls, not a spellcheck. |
| `Break down each change ... before sharing the completed revised excerpt` | Forces it to teach you the edit instead of silently rewriting. This is the part most proofreading prompts miss. |
| `Group these together using Headers` | Keeps a long edit readable instead of one wall of notes. |
| `Trim the fat` | The highest-value line. Most first drafts lose 20 percent of their words here. |
| `Preserve as much of the original tone and style as possible` | The guardrail. Without it, the model rewrites you into generic corporate voice. |
| `informal yet professional` | Swap this if you need something else. `Academic`, `plain language`, or `technical and terse` all work. |

### Ways to remix it

- **Harsher pass:** add `Be blunt. Flag anything that reads as filler, hedging, or corporate jargon.`
- **Keep the length:** add `Do not shorten the piece. Improve it at roughly the same word count.`
- **Compare versions:** add `Show the original and revised sentence side by side in a table.`

---

[Back to the Prompt Playground](../README.md#prompt-playground)
