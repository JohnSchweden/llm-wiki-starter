---
name: create-context-profile
description: Write who the user is into the wiki, so every later chat starts with their context. Use when the user says "create my profile", "teach it who I am", pastes a LinkedIn profile or a CV, or asks the AI to get to know them.
---

# Create Context Profile

One page in `wiki/profile/` that says who the user is, what they work on, and how they want the AI to work with them. This is the first page every later task reads.

## Two ways in

1. **Pasted text.** The user pastes a LinkedIn profile, a CV, an about page, or a bio. Save it unchanged to `raw/profile/<first-name>-linkedin.md` with the raw header (Source, Collected, Published) from `../karpathy-llm-wiki/references/raw-template.md`. Then compile.
2. **Interview.** Nothing to paste. Ask the questions below, one block at a time, in the user's language. Save the answers as `raw/profile/<first-name>-interview.md` with the same header, Source: "interview". Then compile.

If both exist, use both.

## Interview blocks

Ask one block at a time. Three to five questions per block. Skip anything the pasted text already answers. Stop when the user says it is enough.

1. **Who.** Name, role, company or clients, location, languages. How they got here in two sentences.
2. **Work.** What they do all week. The two or three things they are responsible for. What they are working on right now.
3. **Knowledge.** What they know well. What they are learning. Tools they use daily.
4. **Working with AI.** What they already use AI for. What they re-explain in every chat. What the AI should never assume about them.
5. **Voice.** How they want answers: length, language, formality. Words they use. Words they hate.

## Compile

Write `wiki/profile/<first-name>.md` using `../karpathy-llm-wiki/references/article-template.md`:

- Title: the user's name.
- Sources: "Interview, YYYY-MM-DD" and/or "LinkedIn, YYYY-MM-DD".
- Raw: links to the raw files.
- Sections: Who, Work, Knowledge, Working with AI, Voice. Short paragraphs or bullets. Keep the user's own words where they gave them.
- A last section **Standing instructions**: three to seven lines the AI applies in every chat. Example: "Answer in German unless asked otherwise." "Assume I know Python; do not explain basics." "Never pitch tools I did not ask about."

Then update `wiki/index.md` (new topic `profile` if missing, one line: "Who the user is and how to work with them.") and append to `wiki/log.md`:

```
## [YYYY-MM-DD] ingest | <Name> (profile)
```

## Rules

- Do not invent facts. A question the user skipped stays out of the page.
- Show the page before saving. The user approves the profile; it is about them.
- The business side (company, team, clients) belongs in `create-business-context-profile`, not here.
