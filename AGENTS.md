# This folder is an LLM wiki

A knowledge base your AI reads first, so you stop explaining your context in every chat. The AI writes and maintains the wiki. You read it, add sources, and ask questions.

## Layout

- `raw/` holds source material: clipped web pages, pasted text, documents. Never edit a file in here. One subfolder per topic.
- `wiki/` holds the articles the AI writes from `raw/`. One subfolder per topic, one article per concept. `wiki/index.md` lists every article. `wiki/log.md` records every ingest, query and lint.
- `outputs/` holds what the wiki produces: answers, posts, one-pagers, slides.
- `copilot/skills/` holds the skills. A skill is a `SKILL.md` that tells the AI how to do one job. Read a skill's file before doing its job.

## Skills

- `copilot/skills/karpathy-llm-wiki/SKILL.md`: ingest a source into `raw/` and compile it into `wiki/`; answer a question from the wiki; lint the wiki for contradictions, orphans and stale claims. Use it for "add this to the wiki", "what do I know about", "check the wiki".
- `copilot/skills/create-context-profile/SKILL.md`: interview the user, or read a pasted LinkedIn profile, and write who they are into `wiki/profile/`.
- `copilot/skills/create-business-context-profile/SKILL.md`: the same for their company or client.
- `copilot/skills/write-from-wiki/SKILL.md`: write one piece in the user's voice from the profile and the wiki into `outputs/`.

## Rules

- Answer from `wiki/` first. Cite the article you used by path, for example `wiki/llm-wiki/llm-wiki-pattern.md`. If the wiki does not know, say so. Do not fill the gap from memory.
- Every ingest updates the article, `wiki/index.md` and `wiki/log.md`.
- Ask before deleting anything.
- Write in the user's language. Keep the user's wording when you quote them.

## Starter content

The wiki ships with one topic, `llm-wiki`, compiled from three sources: Karpathy's post on LLM knowledge bases, his gist "LLM Wiki", and a walkthrough on building a second brain with three folders. Ask it "What is an LLM wiki?" to see a grounded answer. Ask it something it cannot know to see it say so.
