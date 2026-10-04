# retro

## What it does

Looks back at a coding session and suggests changes to the agent's **environment**, not
the code: navigation pointers, automated checks, coding standards, steering-file size,
tool economy, no-op instructions, and information access. A mechanical violation gets a
deterministic check (linter rule, pre-commit hook, CI job); `CODING_STANDARDS.md` is for
genuine judgement calls. A repo with no guardrail at all is a finding in itself.

## When to reach for it

After a session, especially one where the agent got lost, repeated a mistake, or made an
expensive tool call. Explicit-only.

## Signals

- **Working:** findings ordered by severity, each tied to something that happened in the
  session.
- **Not working:** generic advice, or new prose rules for things a linter could enforce.

## Where it fits

Reads the session, then loads `writing-for-agents` for the writing style. It pairs well
with `papercuts`. See the full [SKILL.md](../../../skills/engineering/retro/SKILL.md).
