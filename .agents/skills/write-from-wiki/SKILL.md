---
name: write-from-wiki
description: Write one piece in the user's voice from the wiki into outputs/. Use when the user says "write a post about", "make a one-pager from", "draft an email on", or names anything to write from what the wiki knows.
---

# Write From Wiki

The wiki takes in. This skill gives back: one post, one-pager, email, memo or summary, written from the wiki in the user's voice, saved to `outputs/`.

## Steps

1. **Read the profile first.** Open `wiki/profile/` and the Standing instructions and Voice sections. If there is no profile, say so and offer to run `create-context-profile`. Without a profile the piece is in nobody's voice.
2. **Read the sources.** Open `wiki/index.md`, pick the articles the piece needs, read them. Use only what the wiki says. If the wiki does not cover the topic, say which part is missing. Do not fill it from memory.
3. **Agree the shape.** One line back to the user: format, length, audience, the one point the piece makes. Wait for a yes.
4. **Write.** In the user's language and register. Their words over yours. Short sentences. One idea per paragraph. No filler openers, no closing summary, no lists of three for rhythm, no em dashes.
5. **Save** to `outputs/YYYY-MM-DD-<slug>.md`. First line: the title. Last line: `Sources:` with the wiki articles used, as paths.
6. **Offer the loop.** If the piece contains a new claim or a decision worth keeping, offer to file it back into the wiki with `karpathy-llm-wiki`. That closes the loop: output becomes source.

## Rules

- The wiki is the only source. A claim that is not in the wiki does not go in the piece.
- Show the draft in chat, then save. The user edits; the AI does not publish.
- Never change the wiki from this skill. Ingest is `karpathy-llm-wiki`'s job.
