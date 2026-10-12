# This folder is an LLM wiki

A knowledge base your AI reads first, so you stop explaining your context in every chat. The AI writes and maintains the wiki. You read it, add sources, and ask questions.

## Layout

- `raw/` holds source material: clipped web pages, pasted text, documents. Never edit a file in here. One subfolder per topic.
- `wiki/` holds the articles the AI writes from `raw/`. One subfolder per topic, one article per concept. `wiki/index.md` lists every article. `wiki/log.md` records every ingest, query and lint.
- `outputs/` holds what the wiki produces: answers, posts, one-pagers, slides.
- `.agents/skills/` holds the skills. A skill is a `SKILL.md` that tells the AI how to do one job. Read a skill's file before doing its job.
- `skills/` is a visible mirror for Obsidian, which hides dot folders. It holds one pointer note per skill. Agents read `.agents/skills/`, not this folder.

## Skills

- `.agents/skills/karpathy-llm-wiki/SKILL.md`: ingest a source into `raw/` and compile it into `wiki/`; answer a question from the wiki; lint the wiki for contradictions, orphans and stale claims; write one piece in the user's voice from the profile and the wiki into `outputs/`. Use it for "add this to the wiki", "what do I know about", "check the wiki", "write a post about".
- `.agents/skills/create-context-profile/SKILL.md`: interview the user, or read a pasted LinkedIn profile, and write who they are into `wiki/profile/`.
- `.agents/skills/create-business-context-profile/SKILL.md`: the same for their company or client.
- `.agents/skills/create-design-guide/SKILL.md`: read a pasted brand guide or deck, or interview the user, and write how their work looks into `wiki/profile/design-guide.md`.
- `.agents/skills/create-voice-guide/SKILL.md`: read posts the user wrote, or interview them, and write how they sound into `wiki/profile/voice-guide.md`.
- `.agents/skills/make-slide/SKILL.md`: build one PowerPoint slide from an agreed plan, with no installs. Use it for "build the slide", "make the PowerPoint".

## Rules

- Answer from `wiki/` first. Cite the article you used by path, for example `wiki/llm-wiki/llm-wiki-pattern.md`. If the wiki does not know, say so. Do not fill the gap from memory.
- Every ingest updates the article, `wiki/index.md` and `wiki/log.md`.
- Ask before deleting anything.
- Write in the user's language. Keep the user's wording when you quote them.

## Writing

When the user asks for a post, one-pager, email, memo or summary:

- Read `wiki/profile/` first (profile, voice guide, design guide for decks). No profile, no voice: say so and offer `create-context-profile`.
- The wiki is the only source. Say what it lacks instead of filling the gap from memory.
- Agree the shape in one line (format, length, audience, the one point) before writing.
- Save to `outputs/YYYY-MM-DD-<slug>.md`, title first, `Sources:` last. Show the draft; the user publishes.
- Offer to ingest the piece back into the wiki if it holds a new claim or decision. Output becomes source.

## Starter content

The wiki ships with one topic, `llm-wiki`, compiled from three sources: Karpathy's post on LLM knowledge bases, his gist "LLM Wiki", and a walkthrough on building a second brain with three folders. Ask it "What is an LLM wiki?" to see a grounded answer. Ask it something it cannot know to see it say so.
