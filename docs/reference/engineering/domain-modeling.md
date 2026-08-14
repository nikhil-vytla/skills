# domain-modeling

## What it does

Builds and sharpens a project's domain language while you design: challenges a term
that conflicts with the glossary, forces a precise word where you used a vague one,
stress-tests relationships with concrete scenarios, and cross-references what you say
against what the code does. Resolved terms are written into `CONTEXT.md` inline, the
moment they resolve; decisions are offered as ADRs only when hard to reverse,
surprising without context, and a real trade-off — all three at once. Formats live in
the skill's `CONTEXT-FORMAT.md` and `ADR-FORMAT.md`.

## When to reach for it

When the words are the problem: two people mean different things by the same term, one
term is doing three jobs, or a hard-to-reverse choice just got made. It's model-invoked
and mostly runs underneath `grill-with-docs` or `wayfinder`; type `/domain-modeling`
when you want the discipline without the surrounding interview. If you only want a term
looked up, just read `CONTEXT.md`.

## FAQ

**What belongs in CONTEXT.md?**
Terms and nothing else — what a thing is, in one or two sentences, with rejected
synonyms under `_Avoid_`. No implementation details, no spec, no scratch notes. A
bloating `CONTEXT.md` means decisions leaked in; prune it back to a glossary.

**When does something become an ADR?**
Only when all three gates pass. An easily-reversed decision will just get reversed, an
unsurprising one is nobody's question, and one with no real alternative has nothing to
record. Most sessions produce zero ADRs, and that's it working.

## Signals

- **Working:** it stops you mid-sentence to ask which of two things you meant,
  `CONTEXT.md` changes during the conversation and gets shorter as often as longer, and
  it quotes your code back when your sentence disagrees with it.
- **Not working:** every answer you give gets persisted, turning the glossary into a
  running spec.

## Where it fits

The writing half of `grill-with-docs` (which pairs it with `grilling`) and one of the
skills `wayfinder` invokes while resolving decision tickets. See the full
[SKILL.md](../../../skills/engineering/domain-modeling/SKILL.md).
