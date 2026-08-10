# Check My Calendar

## What This Is

A scheduling prompt that asks Copilot to find open meeting slots across the next 10 business days. It filters out the messy parts of a calendar, adds buffer time, and returns plain text you can paste to someone outside your organization.

Use it when you need to offer availability without manually scanning your calendar.

> [!TIP]
> Adjust the meeting length, business hours, and time zone before you paste it if your schedule needs different constraints.

---

## Quick Copy

```
Check my calendar and list 6–8 open 30–45 minute slots over the next 10 business days, between 9 AM and 4 PM in my time zone. Exclude travel, focus time, lunch, and holds. Leave 15 minutes buffer before/after other meetings. Return in plain text I can paste to an external contact, with this format:

- Tue Nov 18, 10:30–11:00 AM CT
- Wed Nov 19, 1:00–1:45 PM CT
- Thu Nov 20, 9:15–10:00 AM CT

Add a closing line: "If none of these work, share a few windows and I’ll send an invite."
```

---

## What each instruction is doing

| Instruction | What it controls |
|---|---|
| `slot count and meeting length` | Gives enough options without flooding the recipient. |
| `next 10 business days` | Keeps the search window useful and near term. |
| `between 9 AM and 4 PM` | Avoids early, late, and awkward times. |
| `Exclude travel, focus time, lunch, and holds` | Protects calendar blocks that should not become meeting slots. |
| `plain text I can paste` | Makes the output ready for email or chat. |

---

[Back to the Prompt Playground](../README.md#prompt-playground)


