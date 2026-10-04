# tdd

## What it does

The reference that makes the red → green loop produce tests worth keeping: what a good
test is, where tests go, the anti-patterns, and the rules of the loop. It also covers
mocking (`mocking.md`) and test shape (`tests.md`). It reads `GLOSSARY.md` so test names
match the domain language, and defers to `codebase-design` when the interface shape is
in question.

## When to reach for it

Building a feature or fixing a bug test-first, or when you want integration tests.
Model-invoked, and `implement-spec` calls it once per ticket.

## Signals

- **Working:** one failing test at a time, tests that exercise behavior through the
  public interface, and tests that survive a refactor.
- **Not working:** tests written in bulk after the code, or tests coupled to internals.

## Where it fits

Used by `implement-spec` and any ticket-level implementation. See the full
[SKILL.md](../../../skills/engineering/tdd/SKILL.md).
