---
name: create-business-context-profile
description: Write the user's company, team, or client into the wiki, so work tasks start with the business context. Use when the user says "create the company profile", "teach it about my business", "client context", or pastes a company website, org chart, OKRs, or a role description.
---

# Create Business Context Profile

One page per company in `wiki/business/`. It covers the company, the user's role in it, the team, the current priorities, and how people there communicate. Modelled on the five-block context interview used in AI-first operating setups.

## Two ways in

1. **Pasted material.** A website text, a pitch, an org chart, OKRs, a role description. Save each unchanged to `raw/business/<company>-<what>.md` with the raw header from `../karpathy-llm-wiki/references/raw-template.md`. Then compile.
2. **Interview.** Ask the questions below, one at a time, in the user's language. Save the answers to `raw/business/<company>-interview.md`. Then compile.

A client gets its own page, same procedure, same folder.

## Interview blocks

Ask one question at a time. Wait for the answer before the next question. Skip what the pasted text already answers. Check each block with the user before moving on.

1. **Company.** Name, what it sells, to whom, size, where. What makes it different in one sentence. Stage: starting, growing, steady.
2. **Role.** The user's title and what the title means in practice. Who they report to. What they decide alone, what needs sign-off.
3. **Team.** Who works with the user, by role. Who they depend on. Who depends on them. Outside parties that matter: clients, partners, suppliers.
4. **Priorities.** The three things that matter this quarter. The one number the company watches. What is blocked and why.
5. **Communication.** How decisions get made and written down. Tone inside the company. Words and acronyms everyone uses. Topics to handle with care.

## Compile

Write `wiki/business/<company>.md` using `../karpathy-llm-wiki/references/article-template.md`:

- Title: the company name.
- Sources and Raw as in the template.
- Sections: Company, Role, Team, Priorities, Communication. Bullets are fine. Keep the user's wording for names, products and internal terms.
- A last section **Standing instructions**: three to seven lines the AI applies to every task for this company. Example: "Write for the CFO; lead with the number." "The product is called Orbit, never 'the platform'." "Do not mention the merger."

Then update `wiki/index.md` (new topic `business` if missing, one line: "The companies and clients the user works with.") and append to `wiki/log.md`:

```
## [YYYY-MM-DD] ingest | <Company> (business profile)
```

## Rules

- Do not invent facts. A skipped question stays out.
- Show the page before saving. If anything is confidential, the user says so and it stays in the interview, not on the page.
- The user's own profile lives in `wiki/profile/`, written by `create-context-profile`. Link to it from the Role section.
