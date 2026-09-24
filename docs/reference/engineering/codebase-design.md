# codebase-design

## What it does

Holds the shared vocabulary for designing **deep modules**: a lot of behavior behind a
small interface, placed at a clean seam, testable through that interface. The terms are
**module**, **interface**, **implementation**, **adapter**, **depth**, **seam**,
**leverage**, and **locality**. The principles are the deletion test, "the interface is
the test surface", and "one adapter means a hypothetical seam, two means a real one".

It also carries the testability rules: accept dependencies instead of creating them,
return results instead of producing side effects, keep the surface area small. Two
companion docs go deeper. `DEEPENING.md` covers deepening a cluster given its
dependencies. `DESIGN-IT-TWICE.md` spins up parallel sub-agents to design an interface
several radically different ways, then compares them on depth, locality, and seam
placement.

## When to reach for it

When you're designing or reviewing a module's interface, deciding where a seam goes, or
making code more testable and AI-navigable. Also when another skill needs the vocabulary.
Model-invoked, so it can fire on its own when the task fits.

## FAQ

**Why insist on these exact words?**
Because "component", "service", "API", and "boundary" are overloaded, and drifting
between synonyms is what makes an architecture discussion muddy. Consistent language is
the whole point.

**What's the difference between deep and shallow?**
Depth is leverage at the interface: how much behavior a caller or test can exercise per
unit of interface they must learn. Deep is a small interface over a large implementation.
Shallow is an interface nearly as complex as what it hides.

**What's the deletion test?**
Imagine deleting the module. If complexity vanishes, it was a pass-through. If complexity
reappears across N callers, it was earning its keep.

**Is "interface" just a TypeScript `interface`?**
No. It's everything a caller must know: the type signature plus invariants, ordering
constraints, error modes, configuration, and performance characteristics.

## Signals

- **Working:** suggestions get smaller interfaces, the vocabulary shows up in issues and
  refactor proposals, and seams are defended by "what actually varies".
- **Not working:** "component", "service", or "boundary" creep back in, and seams are
  introduced speculatively.

## Where it fits

The foundation `improve-codebase-architecture` calls for its vocabulary and
design-it-twice pattern. See the full
[SKILL.md](../../../skills/engineering/codebase-design/SKILL.md).
