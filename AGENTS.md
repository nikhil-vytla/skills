# AGENTS.md

Shared rules for any agent (Claude Code, Codex) working in this repo. This is the
canonical file — `CLAUDE.md` just points here.

## What this repo is

Nikhil's personal agent skills and workflows: `skills/<category>/<name>/SKILL.md`,
grouped into `engineering/`, `research/`, and `productivity/`. Categories are plain
organizational folders, not skills themselves — there is no category-root `SKILL.md`.

- `docs/guide/` — a short walkthrough of using this repo's skills and playbooks
  together, for humans (start at `docs/guide/README.md`).
- `docs/reference/<category>/<name>.md` — a paragraph on what each real skill does and
  when to reach for it.
- `.agents/adr/` — why the repo is shaped the way it is.
- `.agents/maintenance.md` — the runbook for operating this repo (adding/retiring a
  skill, cutting a release, running sync).

## Skill conventions

- Frontmatter is the Agent Skills spec minimum: `name`, `description`. Add
  `disable-model-invocation: true` for skills that should only fire when typed
  explicitly (e.g. `bro`), never automatically.
- Skills adapted verbatim from another repo carry a `metadata.source` link back to the
  original file plus `metadata.license`. Don't edit borrowed skill content beyond
  adding that metadata block — if it needs to diverge from upstream, note that in the
  changeset instead of silently drifting.
- Keep descriptions short and specific — they're the routing signal for model-invoked
  skills, not documentation. See `.agents/maintenance.md` for the full add/retire
  procedure.

## Playbooks

`engineering/` and `research/` each have a `playbooks/` folder: plain markdown files
(no frontmatter, not auto-discovered as skills) describing the steps for a recurring
task shape. They're reference docs, not invocable skills — route to one by reading its
file directly when the task matches.

## Routing

- Engineering task in a codebase that already exists → `skills/engineering/playbooks/existing-repo.md`
- Engineering task starting a project/package from nothing → `skills/engineering/playbooks/scaffold-new.md`
- Investigating model or inference behavior → `skills/research/playbooks/inference-research.md`
- Building or running an eval → `skills/research/playbooks/evals.md`
- Design question needing a cheap concrete artifact to react to → `prototype` skill
- Work bigger than one session, needs charting as decision tickets first → `wayfinder` skill
- Cleaning up writing → `unslop` skill (applies by default to any prose this repo produces)
- Want the last message restated in plain language → `bro` skill

If a task doesn't match any playbook or skill above, say so rather than forcing it into
the closest match — that's the signal a new playbook or skill is needed.

## Deprecation

A retired skill is deleted, not archived. The changeset that removes it names whatever
replaced it. `skills/deprecated/README.md` documents this policy and otherwise stays
empty.

## Sync

This repo is the source of truth; `scripts/sync-skills` discovers every `SKILL.md`
under `skills/` (regardless of category nesting, excluding `deprecated/`) and symlinks
each one flat, by name, into `~/.claude/skills/<name>` and `~/.agents/skills/<name>`.
Run it after adding, renaming, or removing a skill. It's idempotent, prunes links for
skills that no longer exist, and never touches a file or symlink it doesn't manage.

## Versioning

This repo uses `changesets`. Run `npx changeset` when a change lands, `npx changeset
version` to bump `package.json` and write `CHANGELOG.md` when cutting a release. No
publish step — this isn't an npm package.
