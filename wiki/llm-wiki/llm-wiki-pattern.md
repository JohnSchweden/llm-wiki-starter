# LLM Wiki Pattern

> Sources: Andrej Karpathy on X, 2026-04-02; Andrej Karpathy, gist "LLM Wiki", Unknown
> Raw: [LLM Knowledge Bases](../../raw/llm-wiki/2026-04-02-karpathy-llm-knowledge-bases.md); [LLM Wiki gist](../../raw/llm-wiki/karpathy-llm-wiki-gist.md)

## Overview

An LLM wiki is a folder of markdown files that an AI writes and maintains from a folder of sources you collect. You curate the sources and ask the questions. The AI does the reading, summarising, cross-linking and bookkeeping. Because the AI merges each new source into stable pages instead of re-reading everything per question, the knowledge compounds: the hundredth source lands in a wiki that already knows the first ninety-nine.

## Three layers

- **raw/**: the sources. Articles, papers, posts, transcripts, images. The AI reads them and never edits them.
- **wiki/**: the articles. One page per concept, cross-linked, with an index that lists every page and a log that records every change. Owned by the AI.
- **The schema file**: `AGENTS.md` or `CLAUDE.md` at the root. It tells the AI what the folder is, how it is organised, and what the rules are. This file is what turns a chat model into a librarian.

## Three operations

- **Ingest**: a new source goes into `raw/`. The AI reads it, updates every affected page, adds new pages for new concepts, notes contradictions with the source named, and updates the index and the log.
- **Query**: you ask a question. The AI reads the index, opens the relevant pages, and answers from them, citing the pages. A good answer can be filed back into the wiki as a new page.
- **Lint**: a health check. The AI looks for pages that contradict each other, claims no source backs, orphan pages nobody links to, and concepts that are mentioned often but have no page.

## Why it beats retrieval for personal knowledge

Classic retrieval finds fragments per question and forgets them afterwards. The wiki keeps the synthesis. Contradictions get resolved once and stay resolved. The wiki is plain text in a folder, so it works in any editor, any agent, and in git with full history. Obsidian gives it a graph view and a place to read.

## What the human does

Pick the sources. Direct the analysis. Ask the questions. Think about what it means. Karpathy's own line: the tedious part of a knowledge base was never the reading or the thinking, it was the bookkeeping. The AI does the bookkeeping.

## See Also

- [Second Brain Setup](second-brain-setup.md): the same pattern as a two-minute folder setup.
