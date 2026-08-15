---
name: papercuts
description: Log small frictions the moment they happen, using the papercut CLI bundled with this skill. Use when a tool call misses and gets retried, a command flakes, a cache goes stale, an error misleads, or a setup step confuses — even though none of it is blocking.
---

# Papercuts

When you hit a small friction while working, log it with the bundled
[`scripts/papercut`](scripts/papercut) (path relative to this skill's directory) and
carry on:

```bash
scripts/papercut log "what you were doing → what got in the way"
```

Log in the moment, proactively — none of these are blocking on their own, but logged
together they show where the repo needs sanding down.

## Opt-in, per repo

The log is `PAPERCUTS.jsonl` at the repo's git root (or `$PAPERCUTS_FILE` if set).
`log` refuses to run until the file exists; the user opts a repo in with
`papercut init`. If the tool says the repo hasn't opted in, do **not** create the
file yourself — mention the papercut in your reply instead and move on.

## What counts

- A tool call that missed and had to be retried
- A confusing or undocumented setup step
- A flaky command
- A stale cache
- A misleading error
- A non-obvious gotcha

## What doesn't

- Real bugs — file them wherever the project tracks issues (Linear, JIRA, GitHub)
- Decisions — those are ADRs
- Progress notes or session summaries — papercuts are frictions only

## Entry text

One or two sentences: what you were doing → what got in the way. A guess at the cause
or fix is a bonus, not a requirement. The tool adds the timestamp and branch itself.

The file is append-only and written only through the tool — never edit
`PAPERCUTS.jsonl` directly, and never rewrite, dedupe, or prune it. To read it as
markdown, run `papercut list`.

## Mining a whole session

Only when the user explicitly asks (typing `/papercuts` counts): hand the session
transcript to a cheap model — a Haiku subagent, or whatever cheap model is on hand —
with the "What counts" list above, then log each finding via
`papercut log --source sweep "..."`. Never run this sweep unprompted; the default mode
of this skill is the in-the-moment logging above.
