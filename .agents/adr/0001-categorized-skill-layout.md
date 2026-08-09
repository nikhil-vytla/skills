# Categorized skill layout over flat

This repo's skills live under `skills/<category>/<name>/` (`engineering`, `research`,
`productivity`) rather than a flat `skills/<name>/` namespace like steipete/agent-scripts
or cursor/plugins/pstack use. The categories mirror two personas doing the work —
engineering and research — plus a general productivity bucket, and match the shape of
mattpocock/skills, the primary model for this repo's conventions.

Categories are pure organizational folders: there is no category-root `SKILL.md` (see
[0003](0003-playbooks-are-plain-docs-not-skills.md)), so a category can hold any number
of real skills without implying a single entry point through it.
