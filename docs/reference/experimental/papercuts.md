# papercuts

## What it does

Logs small frictions — a retried tool call, a flaky command, a stale cache, a
misleading error, an undocumented setup step — the moment they happen, via a tiny
bash CLI bundled in the skill's `scripts/` directory. Entries are one or two
sentences (what you were doing → what got in the way, guessed fix as a bonus)
appended as JSON lines to a per-repo `PAPERCUTS.jsonl`; the tool adds the timestamp
and branch. None of these are worth stopping for individually; logged together they
show where the repo needs sanding down. `papercut list` renders the log as markdown.

## When to reach for it

You mostly don't — it's model-invoked, and the point is that the agent logs frictions
proactively as it works. Repos participate by choice: `papercut init` creates
`PAPERCUTS.jsonl` at the git root, and until it exists the tool refuses to log
(`$PAPERCUTS_FILE` overrides the location). The one explicit use is `/papercuts` at
the end of a session, which mines the whole transcript for frictions with a cheap
model and logs each with `--source sweep`. The sweep never runs unprompted.

## FAQ

**Why not just file these in the issue tracker?**
Each papercut is below the bar for a ticket, and filing it would cost more than the
friction did. The value is the aggregate: a cheap, zero-ceremony ledger you skim later
to pick what's worth actually fixing — at which point the fix or a real ticket happens
elsewhere, and the entry stays as history.

**Why a CLI writing JSONL instead of the agent appending markdown?**
The tool makes the invariants mechanical instead of prose-enforced: append-only,
consistent shape, timestamps for free, and inline vs sweep entries stay
distinguishable. The script is the only writer of the file, which is what lets
`list` render it with a couple of sed expressions instead of a JSON parser. Markdown
is a view (`papercut list`), never a second stored artifact that could drift.

**Why opt-in per repo instead of logging everywhere?**
A file appearing uninvited in a repo is itself a papercut. Existence of
`PAPERCUTS.jsonl` doubles as the on/off switch, so the agent has a deterministic
check instead of a judgment call. In repos that haven't opted in, frictions get
mentioned in the reply instead of logged.

## Signals

- **Working:** entries appear mid-session at the moment of friction, and each one is
  readable months later without the session context.
- **Not working:** the log drifts into a session diary or decision log, entries only
  show up in end-of-session batches you didn't ask for, or the agent edits
  `PAPERCUTS.jsonl` directly.

## Where it fits

Standalone, and deliberately below its neighbors: real bugs go to the issue tracker,
hard-to-reverse decisions go to ADRs via `domain-modeling` — papercuts catch what's too
small for either. Experimental, so its shape may still change. See the full
[SKILL.md](../../../skills/experimental/papercuts/SKILL.md).
