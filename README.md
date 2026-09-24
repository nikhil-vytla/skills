# skills

Nikhil's personal agent skills and workflows, for Claude Code and Codex.

Skills live under `skills/<category>/<name>/SKILL.md`, grouped into `engineering/`,
`research/`, and `productivity/`. See [`AGENTS.md`](./AGENTS.md) for the full authoring
and routing conventions — `CLAUDE.md` just points there.

- [`docs/guide/`](docs/guide/README.md) — a short walkthrough of using these skills together.
- [`docs/reference/`](docs/reference/) — what each skill does, one page each.
- [`.agents/adr/`](.agents/adr/) — why the repo is shaped the way it is.
- [`.agents/maintenance.md`](.agents/maintenance.md) — the runbook for operating this repo.

## Setup

```bash
npm install
./scripts/sync-skills
git config core.hooksPath hooks
```

`sync-skills` symlinks every skill in this repo, flat by name, into `~/.claude/skills/`
and `~/.agents/skills/`. Re-run it after adding, renaming, or removing a skill. The
`core.hooksPath` line points git at `hooks/pre-commit`, which runs
`./scripts/validate-skills` on every commit to catch a malformed skill before it lands.

## Skills

| category | skill | for |
|---|---|---|
| engineering | [codebase-design](skills/engineering/codebase-design/SKILL.md) | the deep-module design vocabulary the other design skills build on |
| engineering | [domain-modeling](skills/engineering/domain-modeling/SKILL.md) | building a project's glossary and ADRs as decisions crystallise |
| engineering | [grill-with-docs](skills/engineering/grill-with-docs/SKILL.md) | interviewing a plan in a repo while writing CONTEXT.md and ADRs |
| engineering | [improve-codebase-architecture](skills/engineering/improve-codebase-architecture/SKILL.md) | scanning a codebase for deepening opportunities, then grilling through one |
| engineering | [pr-descriptions](skills/engineering/pr-descriptions/SKILL.md) | writing high-signal PR descriptions for stacked PR trains |
| engineering | [prototype](skills/engineering/prototype/SKILL.md) | throwaway code to answer a design question |
| engineering | [research](skills/engineering/research/SKILL.md) | investigating a question against primary sources |
| engineering | [setup-skills](skills/engineering/setup-skills/SKILL.md) | configuring a repo's issue tracker and domain docs for the engineering skills |
| engineering | [to-spec](skills/engineering/to-spec/SKILL.md) | synthesizing the current conversation into a published spec |
| engineering | [to-tickets](skills/engineering/to-tickets/SKILL.md) | breaking a plan into tracer-bullet tickets with blocking edges |
| engineering | [triage](skills/engineering/triage/SKILL.md) | moving issues and incoming PRs through triage roles |
| engineering | [wayfinder](skills/engineering/wayfinder/SKILL.md) | charting work bigger than one session as decision tickets |
| experimental | [clean-copy](skills/experimental/clean-copy/SKILL.md) | cutting interface copy that shouldn't exist |
| experimental | [papercuts](skills/experimental/papercuts/SKILL.md) | logging small frictions with a durable record |
| productivity | [bro](skills/productivity/bro/SKILL.md) | restating the last message in plain language |
| productivity | [grill-me](skills/productivity/grill-me/SKILL.md) | interviewing a loose idea until it's decided, no repo needed |
| productivity | [grilling](skills/productivity/grilling/SKILL.md) | the round-based interview primitive the grill skills run |
| productivity | [show-me](skills/productivity/show-me/SKILL.md) | explaining the current topic visually |
| productivity | [unslop](skills/productivity/unslop/SKILL.md) | cutting AI tells from writing |

## Playbooks

Plain reference docs (not invocable skills) for recurring task shapes — see
`AGENTS.md`'s Routing section for when to use each.

| category | playbook | for |
|---|---|---|
| engineering | [existing-repo](skills/engineering/playbooks/existing-repo.md) | changing code in a codebase that already exists |
| engineering | [scaffold-new](skills/engineering/playbooks/scaffold-new.md) | starting a project or package from nothing |
| research | [inference-research](skills/research/playbooks/inference-research.md) | investigating model or inference behavior |
| research | [evals](skills/research/playbooks/evals.md) | building or running evals |

## Deprecation

A retired skill is deleted, not archived — see [`skills/deprecated/README.md`](skills/deprecated/README.md).

## Versioning

This repo uses [changesets](https://github.com/changesets/changesets). Run `npx changeset`
when a change lands, `npx changeset version` to cut a release. See [`CHANGELOG.md`](CHANGELOG.md).

## License

[MIT](LICENSE)
