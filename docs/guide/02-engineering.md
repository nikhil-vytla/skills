# Engineering

Two playbooks cover the shape of most engineering tasks:

- [existing-repo](../../skills/engineering/playbooks/existing-repo.md) — changing code
  in a codebase that already exists.
- [scaffold-new](../../skills/engineering/playbooks/scaffold-new.md) — starting a
  project or package from nothing.

Within either, reach for:

- [`setup-skills`](../reference/engineering/setup-skills.md) once per repo, before any
  of the below. It configures the issue tracker and domain docs the others read.
- [`triage`](../reference/engineering/triage.md) to move issues and incoming PRs
  through triage roles and produce agent-ready briefs.
- [`to-spec`](../reference/engineering/to-spec.md) to turn the current conversation into
  a spec published to the tracker.
- [`to-tickets`](../reference/engineering/to-tickets.md) to break a spec or plan into
  tracer-bullet tickets with blocking edges.
- [`prototype`](../reference/engineering/prototype.md) when a design question needs a
  cheap concrete artifact to react to before committing to a shape.
- [`wayfinder`](../reference/engineering/wayfinder.md) when the task is bigger than one
  session and needs to be charted as decision tickets before any of it gets built.
- [`grill-with-docs`](../reference/engineering/grill-with-docs.md) when the plan is
  still fuzzy and worth an interview that writes the vocabulary (`CONTEXT.md`) and
  hard decisions (ADRs) into the repo as it goes.
- [`domain-modeling`](../reference/engineering/domain-modeling.md) fires on its own
  when terminology or ADRs are being changed. It's the writing half of
  `grill-with-docs`.
- [`improve-codebase-architecture`](../reference/engineering/improve-codebase-architecture.md)
  to survey a codebase for deepening opportunities and grill through the one you pick.
- [`codebase-design`](../reference/engineering/codebase-design.md) fires when a module's
  interface is being designed. It's the shared deep-module vocabulary.
- [`research`](../reference/engineering/research.md) to investigate a question against
  primary sources.

Next: [Research](03-research.md).
