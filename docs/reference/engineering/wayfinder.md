# wayfinder

## What it does

Charts work too big for one agent session as a shared map of decision tickets on an
issue tracker, then resolves them one at a time until the way forward is clear. Plans
by default — each ticket resolves a decision, not a slice of a build — and stops once
nothing is left to decide before someone does the work.

## When to reach for it

When a loose idea arrives wrapped in fog: the destination isn't visible yet and the
effort spans more than one session. User-invoked only
(`disable-model-invocation: true`) — type `/wayfinder` explicitly.

## FAQ

**The scope feels small enough to just start building — do I still need a map?**
No. If grilling the frontier breadth-first surfaces no fog, the whole journey fits one
session — stop and ask how to proceed instead of charting one anyway.

**Can I resolve more than one ticket per session to move faster?**
Only research tickets. Everything else is one ticket per session by design, since other
sessions may be editing the tracker concurrently and claiming keeps them from
colliding.

## Signals

- **Working:** every ticket resolves a decision, not a deliverable; the frontier (open,
  unblocked, unclaimed tickets) is always visible in the tracker's own UI via native
  blocking, without opening the map.
- **Not working:** the "Not yet specified" section got pre-sliced into ticket-sized
  pieces before the question was sharp; tickets are being resolved out of order without
  claiming first.

## Where it fits

Uses `prototype` as one of its four ticket types (Research / Prototype / Grilling /
Task) when the blocking question is about look or behavior. See the full
[SKILL.md](../../../skills/engineering/wayfinder/SKILL.md) for ticket types, the map
format, and both invocation modes (charting the map vs. working through it).
