# Sync script mirrors skills, not a plugin manifest

Claude Code only auto-discovers `SKILL.md` one level deep under `skills/`, so a
categorized layout needs either an explicit manifest enumerating every skill's path
(mattpocock's `.claude-plugin/plugin.json`, distributed through Claude Code's plugin
marketplace) or a script that mirrors the real, nested layout into a flat directory
Claude Code can scan (steipete/agent-scripts' `scripts/sync-skills`).

This repo isn't distributed to anyone else, so the ceremony of a versioned,
marketplace-listed plugin manifest doesn't buy anything. `scripts/sync-skills` mirrors
skills into `~/.claude/skills/` and `~/.agents/skills/` instead.

The script itself is modeled on mattpocock's own maintainer-only
`scripts/link-skills.sh`: a single `find` over `skills/` (excluding `deprecated/`)
discovers every skill regardless of nesting depth and symlinks each one flat, by name,
into both directories — rather than splitting behavior by harness the way steipete's
script does (whole-category links for Codex, flat links for Claude). One discovery
mechanism for every harness is simpler to reason about and needs no hardcoded category
list.
