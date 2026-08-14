# grill-me

## What it does

Takes a loose idea — a feature, a product direction, a business call, a piece of
writing — and interviews you about it until you could commit to it. It runs a
`/grilling` session: questions arrive in rounds, each round covering every question
whose prerequisites you've already settled, with a recommended answer attached to each.
It's stateless — no repo needed, no files written; what it leaves behind is a sharper
version of the idea.

## When to reach for it

As soon as an idea is worth taking seriously and long before it's worked out. Vagueness
is the input, not a reason to wait. Type `/grill-me` explicitly — it never fires on its
own — and start it in a fresh conversation rather than on top of a plan an agent
already wrote. If the subject lives in a repo and you want the session's vocabulary and
decisions written down, use `grill-with-docs` instead.

## FAQ

**How do I know when it's done?**
When the frontier is empty — every branch of the design tree visited, nothing left
silently assumed. Count rounds, not questions; dozens of questions across a few rounds
is an ordinary session.

**What if a question can't be answered by talking?**
Some can't — "how should this feel?" needs something to react to. Stop grilling, build
the throwaway version with `prototype`, then come back and answer in one line.

## Signals

- **Working:** you disagree with something, later rounds clearly build on your earlier
  answers, and you end up somewhere you didn't expect.
- **Not working:** you're nodding "agreed" through every round and the output is a plan
  the agent wrote and you rubber-stamped.

## Where it fits

A one-line wrapper over the `grilling` primitive — it doesn't work without that skill
installed. Its stateful sibling is `grill-with-docs`; for efforts too big for one
session, `wayfinder`. See the full
[SKILL.md](../../../skills/productivity/grill-me/SKILL.md).
