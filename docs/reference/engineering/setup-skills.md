# setup-skills

## What it does

Configures one repo for the engineering skills. It explores the repo, then asks how the
repo tracks issues, which label vocabulary triage uses, and where the domain docs live.
It asks one section at a time, leading with its recommended answer. It writes the answers
to `docs/agents/issue-tracker.md`, `docs/agents/domain.md`, and
`docs/agents/triage-labels.md`, then adds an `## Agent skills` block to whichever of
`CLAUDE.md`/`AGENTS.md` already exists. It never creates the other one. Issue-tracker
templates ship for GitHub, GitLab, and a local-markdown `.scratch/` convention, plus a
freeform "other" for Jira/Linear-style workflows.

It's prompt-driven, not a deterministic script. It explores, presents findings, confirms,
then writes. Nothing is installed and no commands run; the output is markdown the other
skills read.

## When to reach for it

The first time you use the engineering skills in a repo, or any time `wayfinder`,
`triage`, `to-spec`, or `to-tickets` tell you the issue tracker or triage vocabulary
hasn't been provided. Explicit-only, so it never fires on its own.

## FAQ

**Do I have to re-run it after editing the config?**
No. Edit `docs/agents/*.md` directly. Re-run only to switch issue trackers or start
over from scratch.

**Which file does the `## Agent skills` block go in?**
`CLAUDE.md` if it exists, else `AGENTS.md`. If neither exists it asks which to create
rather than picking for you, and it updates an existing block in place instead of
appending a duplicate.

**What's the default issue tracker?**
GitHub if the repo's remote is GitHub, GitLab if it's GitLab. Otherwise, or if you
prefer, pick GitHub, GitLab, local markdown, or describe your own workflow in a
paragraph.

**Does triage need anything special?**
Yes. The triage label section only runs when the `triage` skill is installed. Both are
in this repo, so it runs.

## Signals

- **Working:** setup finishes in one pass, and `wayfinder`/`triage`/`to-spec`/
  `to-tickets` find `docs/agents/*.md` without asking where issues live.
- **Not working:** it created a second `CLAUDE.md`/`AGENTS.md`, or skills still prompt
  you for the tracker after it ran.

## Where it fits

The entry point to the engineering flow. See `AGENTS.md`'s routing. Everything that
touches issues or the domain model reads what it writes: `wayfinder`, `triage`,
`to-spec`, `to-tickets`, `domain-modeling`, and `grill-with-docs`. See the full
[SKILL.md](../../../skills/engineering/setup-skills/SKILL.md).
