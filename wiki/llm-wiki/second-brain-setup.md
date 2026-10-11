# Second Brain Setup

> Sources: Nick Spisak on X, 2026-04-04
> Raw: [How to Build Your Second Brain](../../raw/llm-wiki/2026-04-04-how-to-build-your-second-brain.md)

## Overview

The smallest working version of the [LLM Wiki Pattern](llm-wiki-pattern.md): three folders, one schema file, one compile prompt, a query loop and a monthly health check. No database, no special software, no plugins required. Set up in a few minutes.

## Folder layout

- `raw/` for everything you collect. Clips, exports, images. Do not tidy it by hand.
- `wiki/` for what the AI writes. You read, the AI writes.
- `outputs/` for answers, reports and anything the wiki produces. The good ones can be folded back into the wiki.

## The schema file

One file at the root, `AGENTS.md` or `CLAUDE.md`. It says what the knowledge base is about, how the folders work, and the rules: one topic per page, a summary at the top of every page, links between pages, an index the AI keeps current. Flat instructions, no special format.

## The loop

1. Put a source into `raw/`. Paste text, save a web page, or let a browser tool fetch it.
2. Tell the AI to compile: read `raw/`, update `wiki/` following the schema, index first, one page per topic, link the pages.
3. Ask questions across `wiki/`. Save useful answers to `outputs/` or into the wiki itself.
4. Once a month, run a health check: contradictions, unexplained mentions, unsourced claims, gaps.

## Pitfalls

- Errors compound. A wrong answer filed back into the wiki becomes a wrong source. The health check exists for this.
- Tool rabbit holes. A heavy plugin stack is not the system. Flat markdown plus a schema file is.

## See Also

- [LLM Wiki Pattern](llm-wiki-pattern.md): the idea behind the folders.
