# code-review

## What it does

Reviews the diff between `HEAD` and a fixed point you supply (commit, branch, tag, or
merge-base) along two axes in parallel sub-agents: **Standards** (does the code follow
the repo's documented coding standards, plus baseline smells) and **Spec** (does it
implement the originating issue or spec). It aggregates both reports side by side.

## When to reach for it

Reviewing a branch, a PR, or work in progress, or when you say "review since X".
`implement-spec` runs it on the integration branch before closing out.

## Signals

- **Working:** findings cite the standard or the spec requirement they break, and
  hard violations are separated from judgement calls.
- **Not working:** generic style nitpicks that tooling already enforces.

## Where it fits

Needs the tracker config from `setup-skills` to fetch the originating issue. Follows
`implement-spec` or any implementation work. See the full
[SKILL.md](../../../skills/engineering/code-review/SKILL.md).
