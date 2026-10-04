---
"nikhil-skills": minor
---

Sync with [mattpocock/skills](https://github.com/mattpocock/skills) v1.3.1 (MIT).

New, ported verbatim: `tdd` (with `mocking.md`, `tests.md`), `code-review`,
`implement-spec`, `retro` under `engineering/`, plus `writing-for-agents` (which `retro`
depends on) under `productivity/`. `/setup-matt-pocock-skills` references are rewritten
to `/setup-skills`, matching the earlier ports. Upstream's `agents/openai.yaml` files
are not carried over.

Updated: `domain-modeling` and `grilling` re-synced. `grilling` now asks several
numbered questions per round, separated by `---`. Upstream removed em-dashes.

Breaking rename: `CONTEXT.md` / `CONTEXT-MAP.md` / `CONTEXT-FORMAT.md` become
`GLOSSARY.md` / `GLOSSARY-MAP.md` / `GLOSSARY-FORMAT.md` across `domain-modeling`,
`improve-codebase-architecture`, `codebase-design`, `triage`, `setup-skills`, the docs,
and the README. `git mv` an existing `CONTEXT.md` to the new name; the skills only look
for `GLOSSARY.md`.
