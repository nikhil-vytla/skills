---
"nikhil-skills": minor
---

Port four skills verbatim from [mattpocock/skills](https://github.com/mattpocock/skills)
(MIT): `grill-me` and `grilling` under `productivity/`, `grill-with-docs` and
`domain-modeling` (with its `ADR-FORMAT.md` and `CONTEXT-FORMAT.md` support files) under
`engineering/`. `grill-me` and `grill-with-docs` are one-line wrappers over the
`grilling` primitive, so the whole dependency set comes along; this also resolves
`wayfinder`'s previously dangling `/grilling` and `/domain-modeling` references.
Upstream's `agents/openai.yaml` files are deliberately not carried over, matching the
earlier `prototype`/`wayfinder` ports.
