# Maintenance

Runbook for operating this repo. See `.agents/adr/` for why these choices were made.

## Adding a skill

1. Create `skills/<category>/<name>/SKILL.md` with `name` and `description`
   frontmatter (Agent Skills spec minimum). Add `disable-model-invocation: true` if it
   should only fire when typed explicitly.
2. If adapted from another repo, add `metadata.source` (link to the original file) and
   `metadata.license` to the frontmatter. Don't edit the borrowed content beyond that.
3. Add a row to `README.md`'s skill table and a short entry under
   `docs/reference/<category>/<name>.md`.
4. Run `./scripts/validate-skills` (or just commit — the pre-commit hook runs it
   automatically once `core.hooksPath` is set, see below) to catch a malformed or
   duplicate `name`/`description` before it causes a confusing runtime miss.
5. Run `./scripts/sync-skills` to link it into `~/.claude/skills/` and
   `~/.agents/skills/`.
6. Record the change with `npx changeset`.

## Retiring a skill

1. Delete `skills/<category>/<name>/` outright — see
   [0004](adr/0004-delete-not-archive-deprecated-skills.md). Don't move it into
   `skills/deprecated/`.
2. Remove its rows from `README.md` and its page under `docs/reference/`.
3. Run `./scripts/sync-skills` to prune the now-dangling links.
4. Record the change with `npx changeset`, naming whatever replaced it.

## Cutting a release

1. Make sure every landed change has a changeset (`npx changeset` if not).
2. Run `npx changeset version` — bumps `package.json` and writes `CHANGELOG.md`.
3. Commit the result.

## Running sync-skills

`./scripts/sync-skills` discovers every `SKILL.md` under `skills/` (excluding
`deprecated/`) via `find`, regardless of category nesting, and symlinks each flat, by
name, into `~/.claude/skills/` and `~/.agents/skills/`. It's idempotent and prunes
managed links for skills that no longer exist. Re-run it any time skills are added,
renamed, or removed.

If a destination directory is itself a symlink into this repo, the script refuses to
run — remove that symlink first (`rm ~/.claude/skills` or `rm ~/.agents/skills`) so it
can recreate it as a real directory.

## Running validate-skills

`./scripts/validate-skills` checks every `skills/**/SKILL.md` (excluding
`deprecated/`) for a well-formed frontmatter block with non-empty `name` and
`description` fields, and fails on duplicate skill names across the repo. Pure bash +
awk — no YAML parser, no interpreter beyond what `sync-skills` already needs.

It runs automatically on `git commit` once hooks are pointed at this repo's `hooks/`
directory — a one-time step per clone:

```bash
git config core.hooksPath hooks
```

Without that, run it manually before committing a new or edited skill.
