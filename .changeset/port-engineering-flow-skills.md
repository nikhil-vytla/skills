---
"nikhil-skills": minor
---

Port seven engineering skills verbatim from
[mattpocock/skills](https://github.com/mattpocock/skills) (MIT): `setup-skills` (renamed
from upstream's `setup-matt-pocock-skills`), `triage` (with `AGENT-BRIEF.md` and
`OUT-OF-SCOPE.md`), `to-spec`, `to-tickets`, `improve-codebase-architecture` (with
`HTML-REPORT.md`), `codebase-design` (with `DEEPENING.md` and `DESIGN-IT-TWICE.md`), and
`research`.

`setup-skills` is the one rename. Upstream's name is branded to its author, and renaming
resolves the dangling `/setup-matt-pocock-skills` references already carried by the
verbatim `wayfinder` port and by the newly ported `triage`, `to-spec`, and `to-tickets`.
Those four references are rewritten to `/setup-skills`; with `codebase-design` and
`research` also brought in, the port leaves no dangling skill references in the flow.
`triage-labels.md` gains the two category roles (`bug`, `enhancement`) that `triage`
applies alongside its five state roles. Upstream's `agents/openai.yaml` packaging files
are deliberately not carried over, matching the earlier `prototype`/`wayfinder` ports.
