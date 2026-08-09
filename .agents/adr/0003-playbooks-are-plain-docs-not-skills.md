# Playbooks are plain reference docs, not skills

The original design borrowed cursor/plugins/pstack's `poteto-mode` pattern directly: a
sticky entry-point skill per category (`skills/engineering/SKILL.md`,
`skills/research/SKILL.md`) that owns a `playbooks/` folder and routes to the matching
playbook by task shape.

Building it surfaced a conflict with
[0001](0001-categorized-skill-layout.md): mattpocock's category folders are purely
organizational, with no category-root `SKILL.md`, and a router skill sitting at the
category root broke that. It also collided on names once flattened for Claude Code —
two category-root skills named after their category can't both become a uniquely-named
entry under a flat mirror without renaming one away from its natural name.

The fix: playbooks (`skills/engineering/playbooks/*.md`,
`skills/research/playbooks/*.md`) stay as plain markdown files with no frontmatter,
never auto-discovered as skills by either harness. `AGENTS.md`'s Routing section points
at the right playbook by task shape instead of a skill doing the routing.
