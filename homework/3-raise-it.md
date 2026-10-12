# 3 Raise it

A scheduled job digests whatever lands in `raw/`. A lint checks the wiki. The loop runs by itself.

Goal: the wiki digests and checks itself while you sleep.

Do this after a week of [1 Feed it](1-feed-it.md). Let the loop run by itself only once you trust what it writes.

## Steps

- [ ] Type: "Set up a scheduled job that runs every evening at 21:00 and digests everything new in raw/ into the wiki. Use launchd on macOS or Task Scheduler on Windows. Show me what you will create before you create it." Read what it shows you, then approve.
- [ ] The job needs the agent on the command line: Claude Code (`claude`) or Codex (`codex`). If the agent says it is missing, let it install it.
- [ ] Type: "Add a lint of the wiki to the same job, once a week on Sunday. Write the findings to outputs/." The lint finds broken links, contradictions and stale pages.
- [ ] Type: "Run the job once now." Check `wiki/log.md` for the new entry.
- [ ] Leave the laptop on at that hour, or move the time to when it is on.

## Every week

- [ ] Read the lint findings in `outputs/` and decide what to fix. The agent proposes, you decide.

## Done when

- [ ] `wiki/log.md` shows an ingest you did not start.

To stop it: "Remove the scheduled job you set up for this wiki."
