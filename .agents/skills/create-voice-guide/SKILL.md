---
name: create-voice-guide
description: Write how the user speaks and writes into the wiki, so every post, email or memo sounds like them. Use when the user says "create my voice guide", "teach it how I speak", "write like me", or pastes posts, emails or talks they wrote.
---

# Create Voice Guide

One page, `wiki/profile/voice-guide.md`, that says how the user sounds. The write operation of `karpathy-llm-wiki` reads it before it writes anything in the user's name.

## Two ways in

1. **Samples.** Three to five posts, emails or talk scripts the user wrote. Save them unchanged to `raw/profile/voice-samples.md` with the raw header (Source, Collected, Published) from `../karpathy-llm-wiki/references/raw-template.md`, one sample per section. Read them for: sentence length, how a piece opens, how it closes, words that come back, words that never appear, how the register shifts per audience. Then compile.
2. **Interview.** Nothing to paste. Ask the questions below, in the user's language. Save the answers as `raw/profile/voice-guide-interview.md` with the same header, Source: "interview". Then compile.

If both exist, use both. Samples beat answers when they disagree; say so.

## Interview

Ask one question at a time. Wait for the answer before the next question. Skip what the samples already answer. Stop when the user says it is enough.

1. **Audience.** Who reads them most. Who else.
2. **Formality.** First names or titles. Jokes or none. "You" or "one".
3. **Length.** How long a post is. How long an email is. One idea or several.
4. **Signature phrases.** Openings and closings they use. Words that are theirs.
5. **Banned words.** Words and phrases that must never appear.
6. **Two examples.** One piece they like, by anyone, and why. One they hate, and why.

## Compile

Write `wiki/profile/voice-guide.md` using `../karpathy-llm-wiki/references/article-template.md`:

- Title: "Voice guide".
- Sources: "Samples, YYYY-MM-DD" and/or "Interview, YYYY-MM-DD".
- Raw: links to the raw files.
- Sections: Audience, Register, Length and rhythm, Words used, Words banned, Openings and closings. Quote the user's own phrases.
- A last section **Standing instructions**: three to seven lines the AI applies to every piece of writing. Example: "Short sentences, one idea each." "Open with the point, never with a greeting." "Never write 'leverage', 'delve' or 'game-changer'."

Then update `wiki/index.md` (topic `profile`, one line: "Voice guide: how the user sounds.") and append to `wiki/log.md`:

```
## [YYYY-MM-DD] ingest | Voice guide (profile)
```

## Rules

- Do not invent a voice. Every rule traces to a sample or an answer.
- Show the page before saving. The user approves it.
- How the user's work looks belongs in `create-design-guide`, not here.
