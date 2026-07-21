# Copilot in PowerPoint Skills Pack

## What This Is

Copilot in PowerPoint lets you save custom skills: reusable instructions you call by name instead of retyping the same request every time. This pack gives you 11 skills for the slide work I do most, from branding and cleanup to summaries, speaker notes, turning a doc into a deck, plain-language rewrites, accessibility, and prepping a deck to go out the door. Drop them in, tweak a couple of placeholders, and start calling them.

Each skill is a small folder with a single `SKILL.md` file inside. That is the format Copilot reads: a bit of frontmatter up top (the name and when to use it) and a set of plain instructions below.

> [!TIP]
> Only two skills need an edit before you use them. In `apply-brand-template`, swap the example fonts and colors for your own. In `customer-ready-pass`, set your approved disclaimer wording. Everything else runs as-is.

---

## How to Turn This On in PowerPoint

Custom skills live in a special OneDrive folder that Copilot in PowerPoint reads from. You set that folder up once, right from the Copilot pane, then drop these skills in. Here is the whole flow.

> [!IMPORTANT]
> You need Copilot in PowerPoint for this. If you don't see Copilot in the app, it isn't part of your Microsoft 365 subscription or your organization hasn't turned it on yet.

### 1. Create your OneDrive skills folder

1. Open a presentation and open the Copilot pane.
2. Select the Settings menu, the **...** in the upper-right corner of the pane.
3. Select **Manage skills**.
4. Select **Custom skills**.
5. Select **Create OneDrive folder**. Copilot creates the skills folder in your OneDrive.
6. Select **Open skills folder** to open it.

### 2. Add these skills

Copy the skill folders from this pack into that OneDrive folder. Keep one folder per skill, each with its `SKILL.md` inside and the folder named to match the `name` in the file. Back in the **Custom skills** dialog, select **Refresh** so Copilot picks them up.

### 3. Use a skill

- Select the **+** menu in the Copilot prompt field, choose **Choose skills**, and pick the one you want.
- Or call it straight from your prompt with an @mention, like `@executive-summary-slide`.
- Toggle any skill on or off from **Manage skills**.

> [!NOTE]
> Added or renamed a skill in OneDrive? Hit **Refresh** in the Custom skills dialog so Copilot sees it. To hide a skill without deleting it, rename its folder so it no longer matches the `name` in its `SKILL.md`. Copilot skips folders that don't match.

> [!TIP]
> Want the official walkthrough with screenshots of each step? See [Copilot in PowerPoint skills](https://support.microsoft.com/en-us/powerpoint/copilot/copilot-in-powerpoint-skills) on Microsoft Support. Format spec: [Agent Skills specification](https://agentskills.io/specification).

---

## What's In The Pack

| Skill | What it does |
|---|---|
| **apply-brand-template** | Reformat slides to your fonts, colors, and logo |
| **fix-this-slide** | Clean up one slide's layout, spacing, and bullets |
| **executive-summary-slide** | Generate a one-slide TL;DR of the whole deck |
| **speaker-notes** | Write presenter notes into the notes pane |
| **doc-to-deck** | Turn a document or notes into a structured deck |
| **de-jargon** | Rewrite slides in plain language |
| **tighten-copy** | Shorten bullets and cut filler |
| **consistency-check** | Audit fonts, colors, caps, and spacing |
| **accessibility-pass** | Alt text, contrast, font size, reading order |
| **customer-ready-pass** | Strip internal content and prep a deck to share |
| **qbr-builder** | Structure content into a QBR flow |

---

## apply-brand-template

Reformats selected slides to your visual identity. Edit the brand tokens at the top first so it uses your fonts, colors, and logo spot.

```markdown
---
name: "apply-brand-template"
description: "Use when the user asks to apply the brand, make slides on-brand, reformat to the template, or standardize formatting across selected slides or the whole deck. Reformats slides to a defined visual identity (fonts, colors, layout, logo)."
---

# Apply Brand Template

Reformats the selected slides (or the whole deck if none are selected) to a consistent brand look.

## Brand tokens — EDIT THESE to match your brand
- Title font / size: Arial, 32pt, Bold
- Body font / size: Arial, 18pt, Regular
- Primary color (titles/accents): #2563EB
- Secondary color: #505050
- Background: White (#FFFFFF)
- Logo placement: bottom-right, small, on every slide except the title slide

## What to do
1. Set every title to the title font, size, and primary color above.
2. Set all body text to the body font and size; use the secondary color for sub-text.
3. Standardize bullet style, cap at 6 bullets per slide and one line per bullet.
4. Align objects to a consistent grid, even out spacing between elements.
5. Ensure consistent margins so content doesn't touch slide edges.
6. Keep all existing content and meaning, only change formatting, never delete substance.

## Output
The same slides, reformatted. End with a one-line summary of what changed.

## Guardrails
- Do not invent new content or rewrite the message.
- If a slide has an intentional full-bleed image or custom layout, leave its layout intact and only fix fonts and colors.
```

---

## fix-this-slide

The "make this one slide look intentional" skill. Point it at a messy slide and let it align, space, and tighten.

```markdown
---
name: "fix-this-slide"
description: "Use when the user says 'fix this slide', 'clean up this slide', or wants a single slide's layout, spacing, alignment, and bullets tightened without changing the message."
---

# Fix This Slide

Cleans up the current or selected slide so it looks intentional and uncluttered.

## What to do
1. Align all objects (left, top, or center as appropriate), snap to a consistent grid.
2. Even out horizontal and vertical spacing between elements.
3. Cap bullets at 6, rewrite each to a single line (under about 10 words) while keeping meaning.
4. Establish clear hierarchy: one dominant title, then supporting points.
5. Remove redundant or duplicate text, merge overlapping ideas.
6. Ensure text has breathing room and nothing runs off the slide.

## Output
The cleaned-up slide, plus a one-line note of the top 2 or 3 fixes made.

## Guardrails
- Preserve the slide's core message and all key facts and numbers.
- Don't change colors or fonts unless they're clearly broken or inconsistent.
- Don't add new content the user didn't provide.
```

---

## executive-summary-slide

Reads the whole deck and builds a single summary slide an executive can read in 20 seconds.

```markdown
---
name: "executive-summary-slide"
description: "Use when the user asks for an executive summary slide, a one-slide TL;DR, a key-takeaways slide, or a 'so what' slide summarizing the whole deck."
---

# Executive Summary Slide

Reads the entire deck and produces a single, executive-ready summary slide.

## What to do
1. Scan all slides to extract the core narrative.
2. Create one new slide titled "Executive Summary" (insert it as slide 2, after the title).
3. Populate it with:
   - 3 key takeaways, each one line, outcome-focused, no jargon.
   - One recommended next step or the ask, clear and specific.
4. Lead with the "so what," not the process. Write for a busy executive who reads only this slide.

## Output
One new summary slide. Below it (in the chat), list the source slides each takeaway was drawn from.

## Guardrails
- Ground every takeaway in content that's actually in the deck, do not invent claims or numbers.
- Keep it to a single slide. If content overflows, prioritize the 3 highest-impact points.
```

---

## speaker-notes

Writes a real talk track into the notes pane so you're not reading bullets off the screen.

```markdown
---
name: "speaker-notes"
description: "Use when the user asks to write, add, or improve speaker notes / presenter notes for slides, or wants a talk track for the deck."
---

# Speaker Notes

Writes concise presenter notes into the notes pane of each slide.

## What to do
1. For each slide, write speaker notes that:
   - Open with the one key point of the slide.
   - Add 2 or 3 supporting talking points the presenter can expand on.
   - Include a natural transition sentence into the next slide.
2. Target roughly 30 to 45 seconds of speaking per slide (about 60 to 90 words).
3. Use a conversational, spoken tone: short sentences, first person, no bullet-fragment shorthand.
4. Write them into the slide's notes pane, not onto the slide.

## Output
Notes added to each slide's notes pane. End with the estimated total talk time for the deck.

## Guardrails
- Notes should complement the slide, not just read the bullets aloud.
- Don't put speaker notes on the visible slide.
- Keep claims consistent with what's on the slide.
```

---

## doc-to-deck

Turns a document, notes, or pasted content into a clean slide outline you can build on.

```markdown
---
name: "doc-to-deck"
description: "Use when the user wants to turn a document, notes, an outline, or pasted content into slides — 'make this into a deck', 'draft slides from this', 'turn this doc into a presentation'."
---

# Doc to Deck

Converts source content into a clean, logically structured slide outline.

## What to do
1. Read the provided content and identify the main themes.
2. Build a deck with this structure:
   - Title slide (topic and subtitle).
   - Agenda slide (3 to 6 sections).
   - One slide per key idea, a clear title plus 3 to 5 supporting bullets, one line each.
   - Closing or next-steps slide.
3. Keep 5 to 7 content slides unless the user specifies a length.
4. Use parallel, action-oriented bullet phrasing.
5. Note where a chart, diagram, or image would strengthen a slide (as a placeholder line).

## Output
A drafted deck. In the chat, give a quick outline (slide titles) so the user can approve or reorder.

## Guardrails
- Use only the facts in the source content, flag anything you inferred.
- Don't overload slides, move detail into speaker notes if needed.
```

---

## de-jargon

Rewrites slide text in plain language for a non-technical or executive audience, without changing the facts.

```markdown
---
name: "de-jargon"
description: "Use when the user asks to simplify slide language, remove jargon, plain-language the deck, or make text friendly for a non-technical or executive audience."
---

# De-Jargon

Rewrites slide text in plain, direct language a non-specialist can follow.

## What to do
1. Replace jargon, acronyms, and internal shorthand with plain terms (spell out an acronym the first time if it must stay).
2. Convert abstract or buzzword phrasing into concrete, everyday language.
3. Prefer active voice and short sentences.
4. Keep technical accuracy, simplify the wording, not the facts.
5. Apply to titles and bullets across the selected slides (or whole deck).

## Output
The rewritten slides, plus a short list of the jargon terms you swapped and what you changed them to.

## Guardrails
- Never change the meaning or the underlying claim.
- Keep product names, required legal terms, and metrics exact.
- If a term is essential and can't be simplified, keep it and add a 3 to 5 word plain-language gloss.
```

---

## tighten-copy

Cuts filler and long bullets so the slide is scannable. Great before any exec review.

```markdown
---
name: "tighten-copy"
description: "Use when the user asks to tighten slide copy, shorten bullets, cut filler, or make the text punchier and more scannable."
---

# Tighten Copy

Makes slide text lean and scannable without losing meaning.

## What to do
1. Cut every bullet to under about 10 words.
2. Remove filler ("in order to", "it is important to note", "basically", "very", "really").
3. Lead each bullet with a strong verb or the key noun.
4. Delete redundant bullets, merge overlapping points.
5. Cap bullets at 6 per slide. If more, split or move detail to speaker notes.
6. Make phrasing parallel across bullets on the same slide.

## Output
The tightened slides, plus a one-line note on how much was trimmed.

## Guardrails
- Preserve all facts, numbers, and the core message.
- Don't drop a point entirely unless it's a true duplicate, condense instead.
```

---

## consistency-check

Audits the whole deck for the little inconsistencies that make it look rushed: mixed fonts, off-palette colors, caps, spacing.

```markdown
---
name: "consistency-check"
description: "Use when the user asks to check the deck for inconsistencies — mismatched fonts, colors, capitalization, spacing, or off-brand slides — and wants a report or fixes."
---

# Consistency Check

Audits the whole deck for visual and textual inconsistencies.

## What to do
Scan every slide and flag:
1. Fonts: different typefaces or sizes used for the same element (titles, body).
2. Colors: off-palette title or accent colors or inconsistent text color.
3. Capitalization: mixed title case vs. sentence case across titles.
4. Bullets: inconsistent bullet styles, indent levels, or punctuation (some end in periods, some don't).
5. Alignment and spacing: objects that break the grid or uneven margins.
6. Terminology: the same thing named differently across slides.

## Output
A slide-by-slide issue list (Slide number, issue, suggested fix). Then ask: "Want me to apply all the fixes?" and only apply on confirmation, or apply directly if the user already asked you to fix.

## Guardrails
- Report before mass-editing unless the user explicitly said "fix them."
- Don't change intentional design choices (like a deliberately different section-divider style), note them separately.
```

---

## accessibility-pass

Adds alt text, checks contrast and font size, and confirms a logical reading order so the deck works for everyone.

```markdown
---
name: "accessibility-pass"
description: "Use when the user asks for an accessibility check or pass — alt text for images, color contrast, reading order, and legible font sizes across the deck."
---

# Accessibility Pass

Makes the deck more accessible and inclusive.

## What to do
1. Alt text: add concise, descriptive alt text to every image, chart, and non-decorative graphic. Mark purely decorative items as decorative.
2. Contrast: flag any text and background combination below WCAG AA contrast and suggest a compliant color.
3. Font size: flag body text under 18pt and titles under 28pt as hard to read from the back of a room.
4. Reading order: check that the tab and reading order of objects on each slide is logical.
5. Links and color: ensure meaning isn't conveyed by color alone, add labels where it is.

## Output
A checklist of what was fixed and what still needs the user's decision (like contrast color choices), slide by slide.

## Guardrails
- Alt text should describe the content or purpose, not just say "image."
- Don't restyle the whole deck, make targeted accessibility fixes only.
```

---

## customer-ready-pass

Takes an internal deck and preps it to share: strips internal notes and hidden slides, flags anything sensitive, and adds a disclaimer. Set your approved disclaimer wording first.

```markdown
---
name: "customer-ready-pass"
description: "Use when the user wants to make a deck customer-ready or externally shareable — strip internal notes, remove confidential markings, add a disclaimer, and confirm nothing internal-only remains."
---

# Customer-Ready Pass

Prepares an internal deck for safe external sharing.

## What to do
1. Remove internal content: delete internal-only speaker notes, hidden slides, DRAFT or INTERNAL watermarks, and back-channel comments.
2. Scrub sensitive detail: flag anything that looks confidential (internal pricing, roadmap dates under NDA, other parties' names, internal metrics) and ask before removing.
3. Disclaimer: add a footer or closing slide with a standard disclaimer (EDIT to your approved wording): "For discussion purposes only. Subject to change."
4. Contact slide: ensure the closing slide has the right presenter contact info.
5. Final scan: confirm no "TODO", placeholder text, or lorem ipsum remains.

## Output
A cleaned, share-ready deck plus a list of everything removed or flagged for the user's review.

## Guardrails
- When unsure whether something is confidential, flag and ask, never assume it's safe to keep.
- Do not remove substantive relevant content, only internal or sensitive items.
- Respect any sensitivity labels on the file, note if the file appears classified.
```

---

## qbr-builder

Structures content into a clean Quarterly Business Review flow: wins, status, pipeline, risks, and asks.

```markdown
---
name: "qbr-builder"
description: "Use when the user asks to build or structure a QBR (Quarterly Business Review) deck, or reformat content into a QBR flow: wins, pipeline/status, risks, and asks."
---

# QBR Builder

Structures content into a clean Quarterly Business Review deck.

## What to do
Build (or reorganize into) this flow:
1. Title slide: account, quarter, presenter.
2. Executive summary: 3 headline outcomes for the quarter.
3. Wins and progress: what was delivered or achieved, with metrics where available.
4. Adoption or status: current state vs. targets (usage, seats, milestones).
5. Pipeline or roadmap: what's next quarter, key initiatives.
6. Risks and blockers: honest list with owner and mitigation.
7. Asks and next steps: specific asks plus agreed actions with dates.

## What to do with the content
- Pull existing deck or pasted content into the right sections, create placeholder bullets where data is missing and mark them "[NEEDS DATA]".
- Keep each slide to a single message, push detail to speaker notes.
- Lead with outcomes and value, not activity.

## Output
A structured QBR deck plus a short list of the "[NEEDS DATA]" placeholders the user must fill in.

## Guardrails
- Don't fabricate metrics, dates, or commitments, use placeholders instead.
- Keep risks honest but constructive, always pair a risk with a mitigation.
```
