# Delete, don't archive, deprecated skills

mattpocock/skills' `skills/deprecated/README.md` documents that his repo deletes
retired skills outright rather than moving them into the deprecated folder — git
history plus the changeset that removed a skill already gives a full paper trail of
what was removed and why it was replaced.

This repo adopts the same policy for the same reason: `skills/deprecated/README.md`
exists only to document that the bucket is intentionally empty, not to hold old skill
folders.

The alternative — moving a retired skill's folder into `skills/deprecated/<name>/` to
keep it browsable without touching git — was considered and rejected, since it
accumulates dead weight in the working tree and risks someone reaching for a stale
approach instead of the current one.
