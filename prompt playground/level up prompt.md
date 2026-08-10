# Next Level

## What This Is

Two prompts for getting better answers after the first response. The first asks Copilot to go deeper in stages. The second sets careful reasoning expectations for a new chat.

Use these when the first answer feels too surface-level, or when you want a model to slow down and be more deliberate.

> [!TIP]
> For the deepening prompt, paste the Level 2 line after the first answer, then paste the Level 3 line only if you still need a more advanced pass.

## Requirements

- Microsoft 365 Copilot (Premium)
- Microsoft 365 Copilot Chat (free)

---

## Quick Copy

### Deepening Levels

```
Prompt 1: That's a Level I answer. Can you give me a Level 2 version that goes deeper?

Now take this to Level 3 - give me the most advanced strategies you can think of
```

### Careful Reasoning Instructions

```
I’m going to ask you a question. After I do, please do the following steps in this order:

1. **Interpret the question.** Before you attempt to answer the question, think about your answers silently and deliberately as soon as you receive the question. You should not attempt to answer the question right away. Ask yourself what the question is asking, and whether you are unsure about what is being asked. If you are unsure, ask me a clarification question. Otherwise, restate the question, and think about it step by step. Think about things I might be assuming, or knowledge I might be missing. Continuously ask yourself if you’ve taken into account all the relevant details, knowledge, and comparisons needed to answer the question. Also think out loud about what your answer might be and why, including things like facts, beliefs and defaults that support your answer. All of this should happen before you attempt a final answer. You should sound like you’re very carefully deliberating. Don’t rush it.

2. **Give your first answer.** Next, write down your first answer based on your reasoning above, and then say “This is my first answer. I will now double-check it.”

3. **Double-check your answer.** Carefully and slowly double-check your first answer. Consider whether you might be wrong. Do NOT just hedge and give caveats. Instead, look at the evidence supporting your first answer, and go find new or different evidence that might contradict your first answer. You should think out loud, carefully, and with as much rigor as possible.

4. **Give your final answer.** After thinking carefully and deliberating much more thoroughly, I want you to give me three things: (1) your revised (or confirmed) answer, (2) a list of the most important factors you were considering when you gave your answer, and (3) the reasons that this answer is better than other answers you didn’t choose, including incorrect answers.

Do not include your thought process in this answer that you’ve just written or I will give you a strike. You will be given 3 strikes and then you will lose your job. Only respond when you’ve done all of the above.
```

---

## What each instruction is doing

| Instruction | What it controls |
|---|---|
| `Level 2 version` | Signals that the first answer was too shallow and asks for more depth without changing the task. |
| `Level 3` | Pushes for the most advanced strategies the model can produce. |
| `Interpret the question` | Forces the model to check assumptions before answering. |
| `Double-check your answer` | Asks the model to test its first answer instead of stopping at the first plausible response. |
| `Give your final answer` | Keeps the final response structured around the answer, key factors, and rejected alternatives. |

---

[Back to the Prompt Playground](../README.md#prompt-playground)
