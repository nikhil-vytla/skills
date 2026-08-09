# prototype

## What it does

Writes throwaway code that answers a design question — does a state model or piece of
logic feel right, or what should a UI look like. The question decides the shape: a
single self-contained HTML file with free-play buttons and guided walkthroughs for
logic/state questions, or several structurally different UI variants on one route,
switchable from a floating bottom bar, for "what should this look like" questions. No
tests, no persistence, no abstractions — the point is to learn something fast, then
fold the validated decision into the real code and park the prototype itself on a
throwaway branch as evidence.

## When to reach for it

The moment a question can't be settled by talking — an edge case that's hard to hold
in your head, a screen that's hard to picture until a few options sit side by side.
Model-invoked, so it can fire automatically when a task fits, or type `/prototype`
directly.

## FAQ

**Isn't a prototype supposed to be deleted when it's done?**
No — the validated decision gets folded into the real code, but the prototype itself
moves to a throwaway branch as a primary source, not the bin. It's the evidence the
decision came from.

**Can I skip picking a branch (logic vs. UI) and just wing it?**
No — the two branches produce structurally different artifacts, and picking wrong
wastes the whole prototype. If it's genuinely ambiguous and no one's around to ask,
default to whichever matches the surrounding code and say so at the top.

## Signals

- **Working:** the question gets answered in one sitting; a non-developer can drive the
  logic demo and says "wait, that shouldn't be possible"; UI variants disagree about
  structure, not just colour.
- **Not working:** tests got added to the prototype; it's still being built a day
  later; variants only differ in colour or copy.

## Where it fits

`wayfinder` files "prototype" as one of its four ticket types when a map's blocking
question is "how should this look" or "how should it behave" — that's this skill run
against one ticket. See the full
[SKILL.md](../../../skills/engineering/prototype/SKILL.md) for the complete process.
