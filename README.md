# llm-wiki-starter

An empty LLM wiki with three sample sources, two articles and four skills. Open the folder in Obsidian, let an AI agent (Claude Code, Codex or the Copilot plugin) read `AGENTS.md`, and start adding sources. Obsidian hides `.agents/` and `.obsidian/`; the `skills/` folder lists the skills with a pointer note each. After the workshop, start with `homework/README.md`.

`.claude/settings.local.json` lets the agent run the plain file commands the skills use (`ls`, `cat`, `grep`, `cp`, `zip`, `xmllint`, `trash` and the like) and look up installed fonts without asking each time. Anything else, such as the Keynote check through `osascript`, still asks first. The Copilot plugin reads this file; it ignores `.claude/settings.json`.

Built for the workshop "LLM Wiki From First Principles" (Agentic Economy Forum, Build Arena, Berlin, 14 October 2026). Pattern by Andrej Karpathy; wiki skill by Yuhan Lei (MIT, see `.agents/skills/karpathy-llm-wiki/LICENSE`).
