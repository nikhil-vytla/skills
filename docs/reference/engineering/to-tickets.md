# to-tickets

## What it does

Breaks a plan, spec, or conversation into **tickets**: tracer-bullet vertical slices,
each declaring the tickets that block it. A good slice cuts a narrow but complete path
through every layer: schema, API, UI, and tests. It is demoable or verifiable on its
own, fits one fresh context window, and prefactoring comes first.

Wide refactors are the exception. A wide refactor is one mechanical change whose blast
radius touches thousands of call sites, so no single edit lands green. `to-tickets`
sequences those as expand-contract: add the new form beside the old, migrate call sites
in batches, then delete the old form. It presents the proposed breakdown for you to quiz
on granularity, blocking edges, and merges or splits, then publishes. A local tracker
gets one file per ticket under `.scratch/<feature>/issues/`. A real tracker gets one
issue per ticket with native blocking links, labelled `ready-for-agent` unless told
otherwise. It never closes or modifies a parent issue.

## When to reach for it

Once a spec or plan is approved and you need the tickets an agent can pick up, or the
blocking graph that orders them. Explicit-only.

## FAQ

**Vertical vs horizontal slices?**
Vertical. Each ticket delivers end-to-end behavior through every layer. A horizontal
slice of only one layer can't be demoed and hides integration risk.

**What's a blocking edge?**
The other tickets that must finish first. A ticket with no blockers sits on the frontier
and can start immediately.

**Why not do the wide refactor in one ticket?**
Because no single vertical slice can land green when the edit breaks thousands of call
sites at once. Expand-contract keeps CI green batch to batch.

**Does it touch Jira/Linear issues itself?**
It writes to whatever `setup-skills` configured, using the tracker's native blocking or
sub-issue relationship where one exists.

## Signals

- **Working:** each ticket is independently verifiable, the blocking edges are honest,
  and the frontier is obvious.
- **Not working:** tickets are layer slices ("add the DB column", "wire the API"), or
  they carry specific file paths that will rot.

## Where it fits

Typically follows `to-spec`, and uses the tracker config from `setup-skills`. Distinct
from `wayfinder`: wayfinder tickets resolve decisions, while these are slices of work.
See the full [SKILL.md](../../../skills/engineering/to-tickets/SKILL.md).
