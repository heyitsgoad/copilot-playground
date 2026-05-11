# The Copilot Chronicle: Daily AI News Brief

## What This Is

A daily newspaper-styled AI news brief built for Microsoft Copilot Cowork. Every morning it scans the latest external AI industry news across Microsoft Copilot, Anthropic, Google, and OpenAI, plus your internal Microsoft field updates pulled via Microsoft Graph signals from email, Teams, and Viva Engage. The output is a formatted HTML newspaper emailed directly to you, sized for a 5-minute coffee read.

> [!TIP]
> This prompt is built around a specific persona and internal source list. Before running, swap in your own email address, role, and internal search terms. The Field Desk section uses Microsoft Graph to pull from your Outlook and Teams activity, so add any internal newsletters, digests, or community channels you want included in the placeholders below.

---

## Prompt


---
name: daily-news
description: Generates "The Copilot Chronicle" — a daily newspaper-styled HTML morning brief covering external AI industry news (Microsoft Copilot, Anthropic/Claude, Google/Gemini, OpenAI/ChatGPT, broader AI industry) plus internal field updates pulled via Microsoft Graph signals from email, Teams, and Viva Engage. Output is an HTML email with masthead, two-column body, dateline, lead story with drop cap, three section banners, ticker, and footer — emailed directly to you. Every story is hyperlinked to its source.

---

## When to Use

Trigger when you ask Copilot to:

- "Run my daily news"
- "Generate my morning news"
- "Send my daily news brief"
- "Build today's Copilot Chronicle"
- "Run the Chronicle"
- "Give me my AI news for today"

---

## When NOT to Use

- Ad-hoc news searches → use web search directly
- Daily summaries of your schedule and inbox → use your daily briefing prompt
- Stakeholder or leadership communications → use a stakeholder comms prompt
- Account-specific field briefings → use your daily field readout prompt

---

## Workflow

### Step 1: Resolve Today's Date

Set the edition date to your local timezone. Use the following filename and subject format:

- **Filename:** `output/the-copilot-chronicle-YYYY-MM-DD.html`
- **Subject:** `The Copilot Chronicle — [Weekday], [Month] [DD], [YYYY]`

---

### Step 2: Gather Coverage (Run in Parallel)

**External Sources (web search — last 24 to 48 hours):**

- Microsoft Copilot and Microsoft 365 Copilot news
- Anthropic and Claude news
- Google Gemini news
- OpenAI and ChatGPT news
- AI industry and enterprise news

**Internal Sources (Microsoft Graph signals via Outlook and Teams):**

> [!IMPORTANT]
> Replace the placeholders below with your own internal newsletters, digests, community channels, and team updates. Copilot will use Microsoft Graph to pull from your Outlook email and Teams activity based on what you list here.

- `{Add your internal newsletter or field advisory name here}`
- `{Add your team digest or weekly huddle name here}`
- `{Add your internal community or Viva Engage channel here}`
- `{Add any product update emails or leadership comms you want included}`
- `{Add any event or training communications relevant to your role}`

Capture the Outlook `webLink` for every internal item so headlines link directly back to the source.

---

### Step 3: Select Stories

| Section | What to Include |
|---|---|
| **Lead Story** | The single biggest Copilot or AI industry story from the last 24 hours. Include a kicker, headline, deck, drop-cap body, and one pull quote from a primary source. |
| **The AI Industry Beat** | 4 to 6 stories across Anthropic, Google, OpenAI, Microsoft, and broader industry. Two-column layout. |
| **From the Field Desk** | 3 to 8 internal items from Outlook and Teams relevant to your role. Hyperlink to source where available. |
| **The Copilot Tape** | 2 to 4 short hits covering pricing, certifications, governance, admin, or release updates. |
| **Ticker** | 6 to 10 short headlines across all categories. |

If a section has no fresh content, shrink or omit it. Never fabricate stories.

---

### Step 4: Generate the HTML

Style anchors for the newspaper layout:

- **Background:** `#f5efe1` | **Paper:** `#fbf6e9` | **Ink:** `#1a1a1a` | **Accent:** `#a02a2a`
- **Fonts:** Georgia / Old Standard TT serif
- **Masthead:** "The Copilot Chronicle" with tagline *Veritas · Productivitas · Intelligentia*
- **Dateline:** Weekday, full date, role/team context, "Price: One Cup of Coffee"
- **Lead story:** Kicker, linked h2 headline, italic deck, drop-cap first paragraph, pull quote with left red rule
- **Section banners:** Black bar, cream text, letter-spaced
- **Body layout:** Two-column via `column-count: 2`
- **Footer:** Double-rule top, all source publications hyperlinked
- **Link hover:** Red `#a02a2a` underline

---

### Step 5: Hyperlinks (Required)

- **External stories:** Hyperlink the headline, byline, and a "Read more →" tail link
- **Internal Field Desk items:** Hyperlink to the Outlook `webLink`
- **Teams items:** Hyperlink to the chat, channel, or meeting URL
- **Footer:** All source publications listed and hyperlinked
- Never fabricate a link. If no URL is available, render plain text.

---

### Step 6: Save and Send

1. Write the file to `output/the-copilot-chronicle-YYYY-MM-DD.html`
2. Verify the file exists
3. Send via email:
   - **To:** `{your email address here}`
   - **Subject:** `The Copilot Chronicle — [Weekday], [Month] [DD], [YYYY]`
   - **Body:** The saved HTML file
   - **Content type:** HTML

---

### Step 7: Confirm

Reply with the edition date, story count by section, and confirmation that it has been emailed. Do not paste the HTML back into chat.

---

## Style Rules

- Every story must trace to a real source. Never fabricate news, names, numbers, or quotes.
- Crisp, slightly witty voice. Headlines can be punchy but never silly.
- Keep blurbs to 2 to 4 sentences. Lead story gets 3 short paragraphs plus a pull quote.
- If a section has nothing fresh, omit it rather than pad it.

---

## Guardrails

- Do not send the email until the HTML file exists in `output/`
- Do not invent Outlook `webLink` values. Only link items returned from real Graph queries.
- Do not include performance evaluations of named individuals.
- Do not include personal or health data scraped from emails.
