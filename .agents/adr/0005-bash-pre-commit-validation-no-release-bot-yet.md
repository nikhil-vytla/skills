# Bash pre-commit validation; no release bot yet

Comparing CI/PR setups across the three reference repos surfaced two adoptable
patterns, and one deliberately skipped.

**Skill validation** (from steipete/agent-scripts' `scripts/validate-skills` +
`hooks/pre-commit`): checking every skill's frontmatter has non-empty `name` and
`description`, and no duplicate names, is cheap and catches a real failure mode — a
malformed skill silently fails to load rather than erroring loudly. Adopted, but
reimplemented rather than copied: steipete's version is Ruby, glob-based one level
deep (`skills/*/SKILL.md`), matching his flat layout. This repo's version
(`scripts/validate-skills`) is plain bash + awk instead, for three reasons: it matches
`scripts/sync-skills`'s existing style and needs no new interpreter (Ruby) or
dependency (a YAML parser, if written in Node); the actual check — two required
string fields plus a duplicate-name scan over a handful of files — doesn't need a
real YAML parser, just line matching; and a compiled language (Rust, Go) was
considered for raw speed and rejected, since the entire run is dominated by process
startup for a check this small (single-digit-millisecond savings against the cost of
introducing a whole compiler toolchain to an otherwise markdown/bash/npm repo). It's
wired up via `git config core.hooksPath hooks` rather than GitHub Actions CI, since it
needs to catch the problem before a bad commit, not after a push.

**Changesets release-PR bot** (from mattpocock/skills' `.github/workflows/release.yml`,
the standard `changesets/action@v1`): explicitly *not* adopted yet. It automates
opening a version-bump PR on every push to `main` — valuable when releases happen
often and from multiple contributors, since it removes a repeated manual step from a
process with more than one actor. This is a solo repo where cutting a release is a
deliberate, infrequent act; running `npx changeset version` by hand (see
`.agents/maintenance.md`) is one command, and the bot would trade that for reviewing
and merging an auto-opened PR — more moving parts (GitHub Actions, secrets) for a step
that isn't actually painful today. Revisit if this repo ever gets other contributors.
