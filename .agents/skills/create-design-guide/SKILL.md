---
name: create-design-guide
description: Write how the user designs into the wiki, so every deck, picture or one-pager follows their colors, fonts and layout rules. Use when the user says "create my design guide", "teach it how I design", "use my brand", or pastes a brand guide, a deck or a styled post.
---

# Create Design Guide

One page, `wiki/profile/design-guide.md`, that says how the user's work should look. The write operation of `karpathy-llm-wiki` reads it before it makes a deck, a picture or anything with a layout.

## Two ways in

1. **Pasted material.** A brand guide, an existing deck, a styled post, a website. Save it unchanged to `raw/profile/design-guide-source.md` with the raw header (Source, Collected, Published) from `../karpathy-llm-wiki/references/raw-template.md`. Pull the values out of it. Then compile.
2. **Interview.** Nothing to paste. Ask the questions below, in the user's language. Save the answers as `raw/profile/design-guide-interview.md` with the same header, Source: "interview". Then compile.

If both exist, use both.

## Interview

Ask one question at a time. Wait for the answer before the next question. Skip what the pasted text already answers. Stop when the user says it is enough.

1. **Colors.** Background, text, one accent. Hex values if they know them, names if not.
2. **Fonts and sizes.** Headline font, body font. How big a headline is on a slide. Bold or not.
3. **Logo.** Which logo, where it sits, when it stays off.
4. **Layout.** Margins. One idea per slide or dense. Where the headline sits. Left-aligned or centered.
5. **Pictures.** Photos, drawings, memes, charts. What they never use.
6. **Do and don't.** Three things every piece must have. Three things that must never appear.

## Compile

Write `wiki/profile/design-guide.md` using `../karpathy-llm-wiki/references/article-template.md`:

- Title: "Design guide".
- Sources: "Interview, YYYY-MM-DD" and/or "<material>, YYYY-MM-DD".
- Raw: links to the raw files.
- Sections: Colors, Fonts, Logo, Layout, Pictures, Do and don't. Values exact: hex codes, font names, sizes in px or pt as given.
- A last section **Standing instructions**: three to seven lines the AI applies to every deck or picture. Example: "Dark background `#08090A`, one accent `#C6F52E`, nothing else in color." "Headlines in Playfair Display, regular weight, never bold." "One idea per slide."

Then update `wiki/index.md` (topic `profile`, one line: "Design guide: how the user's work looks.") and append to `wiki/log.md`:

```
## [YYYY-MM-DD] ingest | Design guide (profile)
```

## Rules

- Do not invent values. No hex code, font or size the user did not give or the material does not show.
- Show the page before saving. The user approves it.
- How the user writes belongs in `create-voice-guide`, not here.
