# implement-spec

## What it does

Implements a whole spec in one run. It reads the tickets as a **task graph**, runs
implementer subagents in their own worktrees across the ready **frontier**, merges each
back to a single **integration branch**, then runs `code-review` on it. Each implementer
builds its ticket with `tdd`. A draft PR opens only when the tracker closes work through
PRs or you ask for one.

## When to reach for it

You have a spec and tickets from `to-spec` and `to-tickets` and want them built in
parallel instead of one at a time. Explicit-only.

## Signals

- **Working:** several tickets in flight at once, fast-forward merges, one branch at the
  end with a clean review.
- **Not working:** implementers working off main instead of the integration branch, or
  tickets resolved without being merged.

## Where it fits

Downstream of `to-spec` and `to-tickets`; calls `tdd` and `code-review`. See the full
[SKILL.md](../../../skills/engineering/implement-spec/SKILL.md).
