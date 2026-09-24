# triage

## What it does

Moves issues through a small state machine. When the tracker config marks external PRs
as a request surface, they go through the same machine; a PR is an issue with attached
code. Two category roles (`bug`, `enhancement`) and five state roles (`needs-triage`,
`needs-info`, `ready-for-agent`, `ready-for-human`, `wontfix`) make up the machine, and
`setup-skills` maps the canonical role names to real label strings.

For a chosen issue it gathers context, runs two codebase checks (is this already
implemented? has it been rejected before?), recommends a category and state, verifies
the claim (reproduce the bug, run the PR's tests), and grills if the request needs
fleshing out. It writes the outcome back. An agent brief for `ready-for-agent`, defined
in `AGENT-BRIEF.md`, stays durable by stating behavior and contracts rather than file
paths or line numbers, so it survives file renames and refactors. `needs-info` gets
triage notes. A rejected enhancement gets a `.out-of-scope/<concept>.md` entry,
explained in `OUT-OF-SCOPE.md`. Every comment it posts starts with an AI-generated
disclaimer.

## When to reach for it

When you want to clear a backlog, decide what's ready for an agent to pick up, or
handle incoming PRs as requests. Explicit-only, invoked as `/triage` with the work
described in natural language, for example "show me anything that needs my attention".

## FAQ

**What's an agent brief?**
The authoritative spec comment an AFK agent works from. It describes interfaces and
behavioral contracts, never file paths or line numbers, so it stays useful while the
codebase changes around it.

**Where do rejected features go?**
`.out-of-scope/<concept>.md`, one file per concept, and only for rejected enhancements.
A `wontfix` because the feature is already implemented does not go there; that would
poison future dedup checks.

**Does triage ever write code?**
No. It verifies claims and posts briefs. Implementation is someone else's session.

**What if it's a PR?**
A PR counts as an issue with attached code, so it goes through the same roles and
machine. The verification step checks out the diff and runs its tests.

## Signals

- **Working:** every triaged item leaves with a clear next owner and, when ready for an
  agent, a brief someone could actually work from.
- **Not working:** it re-asks questions the reporter already answered, or writes briefs
  full of file paths and line numbers.

## Where it fits

Consumes the issue-tracker and triage-labels config from `setup-skills`, and calls
`grilling` and `domain-modeling` when a request needs shaping. See the full
[SKILL.md](../../../skills/engineering/triage/SKILL.md).
