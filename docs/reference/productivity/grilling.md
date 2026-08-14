# grilling

## What it does

The interview primitive the other grill skills run. It maps the subject as a design
tree — every decision branches into the decisions that hang off it — and works the tree
in rounds. Each round asks the whole frontier: every question whose prerequisites are
settled, numbered, each with a recommended answer. Facts get looked up (dispatching
sub-agents if needed); decisions are always yours. It stops when the frontier is empty
and won't act until you confirm the understanding is shared.

## When to reach for it

Usually you don't type it — it's the only skill in the grill family that's
model-invoked, and it mostly runs because `grill-me`, `grill-with-docs`, or `wayfinder`
invoked it. Type `/grilling` directly when you want the plain interview with nothing
layered on top, or invoke it from a skill of your own instead of writing another
interview.

## FAQ

**Can I get one question at a time instead of rounds?**
Yes — add "When grilling, ask one question at a time." to your global `CLAUDE.md`.

**Doesn't asking a whole round at once lose the questions my answers would raise?**
No — a round only contains questions that don't depend on each other, so no answer in a
round can invalidate another question in it. The next round is recomputed from your
answers, not pre-written.

## Signals

- **Working:** rounds arrive as numbered lists you can answer by number, later rounds
  ask things the first round couldn't have, and it looks facts up rather than asking
  you for them.
- **Not working:** it dumps every question at once with no recommendations, answers its
  own questions, or starts building before you've confirmed shared understanding.

## Where it fits

The primitive under `grill-me` and `grill-with-docs` (both one-line wrappers that don't
work without it) and the session `wayfinder` runs inside its decision tickets. See the
full [SKILL.md](../../../skills/productivity/grilling/SKILL.md).
