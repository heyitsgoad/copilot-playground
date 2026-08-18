# Teach-Back Tutor

## What This Is

Reading a 40-slide deck twice is not the same as learning it. This prompt turns a document, presentation, meeting, or project into an active study session. Copilot explains the key ideas in plain language, gives you one realistic workplace example for each, then quizzes you and waits for your answers before it corrects anything.

The magic is in three words: **wait for my answers**. Drop that instruction and Copilot writes the questions and the answers in the same breath, you skim both, and you retain nothing. Keep it and you have to pull the material out of your own head first, which is the part that actually sticks.

Good for onboarding onto a new account, prepping to present someone else's material, or catching up on a project you inherited.

> [!TIP]
> Swap the bracket for the real thing. Attach the file or name the meeting so Copilot grounds the lesson in your actual material instead of teaching you the internet's version of the topic.

---

## Quick Copy

```
Using [document, presentation, meeting, or project] as the source, teach me its key ideas in plain language with one realistic workplace example for each. Then quiz me with five questions, wait for my answers, and explain anything I misunderstand using evidence from the source.
```

---

## Prompt (Full Breakdown)

### Point It at Real Material

`[document, presentation, meeting, or project]`

The whole prompt rests on this one bracket. "Our security policy" is a guess. "The Q3 Security Standards doc in my OneDrive" is a source.

| Source | How to reference it |
|---|---|
| Document | Attach it, or name the file and where it lives |
| Presentation | Name the deck, and say if you only care about certain sections |
| Meeting | Name the meeting and the date so it finds the right recap or transcript |
| Project | Name the project plus the channel, folder, or people the work runs through |

> [!NOTE]
> This works best in a Copilot that can reach your work content, since that is what lets it teach from your deck instead of a generic explainer. No connected content? Attach the file directly in chat and it still works.

---

### Teach, Do Not Summarize

`teach me its key ideas in plain language`

A summary compresses. Teaching unpacks. Those are opposite jobs, and most people ask for the wrong one.

Summaries are great when you already understand the material and just need the highlights. When you do not understand it yet, a summary hands you a shorter version of the thing you already could not follow. "Teach me" tells Copilot to define the terms, explain why the ideas connect, and stop hiding behind the source's vocabulary.

---

### One Example Each

`with one realistic workplace example for each`

Abstract ideas evaporate about four minutes after you read them. An example gives the idea somewhere to live.

Say "realistic" and you get a scenario you could actually walk into. Leave it off and you get textbook filler about a fictional widget company. If the examples still feel generic, push back and say "use examples from my industry" or "use examples from my role."

---

### Five Questions, Then Stop

`quiz me with five questions, wait for my answers`

This is the load-bearing part.

Five is enough to cover the real ideas without turning into a certification exam. The `wait` instruction is what converts the whole thing from reading into recall. You are forced to answer from memory, and the gap between what you thought you knew and what you could actually produce is the useful signal.

Answer honestly. Guessing to look good in front of a chat window is a strange way to waste your own time.

---

### Corrections With Receipts

`explain anything I misunderstand using evidence from the source`

Anyone can be told they are wrong. Being shown where in the deck you went wrong is what fixes it.

This also runs a quiet quality check on the source itself. When Copilot cannot point to evidence for a correction, one of two things is true: it is filling gaps with general knowledge, or the source never actually made that point clearly. Both are worth knowing, especially if you are the one who has to present the thing.

---

### Follow-Up Prompts

- "Ask me five harder questions, but only on the parts I got wrong."
- "Now flip it. I'll teach the material back to you, and you correct me where I'm off."
- "Turn these five questions into a short quiz I can send the team before Thursday's session."
- "What did the source leave unclear or unanswered?"

---

[Back to the Prompt Playground](../README.md#prompt-playground)
