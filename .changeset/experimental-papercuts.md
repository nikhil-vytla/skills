---
"nikhil-skills": minor
---

Add an `experimental/` category for skills still being trialed (looser conventions:
may change shape or be deleted without deprecation ceremony, kept out of `docs/guide/`
until they graduate), and its first skill, `papercuts`: model-invoked in-the-moment
logging of small frictions through a tiny bash CLI (`papercut`, bundled in the skill
directory) that appends JSON lines to a per-repo `PAPERCUTS.jsonl`. Repos opt in via
`papercut init` — the tool refuses to log until the file exists, and `$PAPERCUTS_FILE`
overrides the location. `papercut list` renders the log as markdown; an explicit-only
`/papercuts` sweep mines a whole session transcript with a cheap model and logs
findings with `--source sweep`. Original to this repo — no upstream metadata block.
