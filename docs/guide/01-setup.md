# Setup

```bash
npm install
./scripts/sync-skills
```

`sync-skills` symlinks every skill in this repo, flat by name, into `~/.claude/skills/`
and `~/.agents/skills/`. Re-run it after adding, renaming, or removing a skill — see
`.agents/maintenance.md` for the full runbook.

## Per-repo setup for the engineering skills

Syncing installs the skills, but the engineering skills still need to know how *this*
repo tracks issues, where its domain docs live, and which triage labels it uses. Run
`/setup-skills` once inside any repo where you want to use them; it writes
`docs/agents/issue-tracker.md`, `docs/agents/domain.md`, and
`docs/agents/triage-labels.md`, then points that repo's `CLAUDE.md`/`AGENTS.md` at
them. Re-run it later only to switch issue trackers or start over.

Next: [Engineering](02-engineering.md).
