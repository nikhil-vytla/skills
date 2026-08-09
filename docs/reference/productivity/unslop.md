# unslop

## What it does

Edits writing to remove AI tells (puffery, em-dash overuse, "not just X but Y",
chatbot phrases like "I hope this helps!") and add back a human voice — opinions,
varied rhythm, specificity.

## When to reach for it

Applies by default to any prose this repo or its agent produces — model-invoked, no
explicit trigger needed, though `/unslop` also works directly on a piece of text.

## FAQ

**Doesn't this conflict with technical precision — e.g. keeping a real API name that
happens to sound like jargon?**
No — it targets AI tells (puffery, filler, chatbot phrases), not domain-accurate
technical terms. A real symbol, API name, or measured number stays exactly as is.

## Signals

- **Working:** the rewrite says the same thing, just plainer, with more rhythm
  variation; a self-audit ("what makes this obviously AI generated?") turns up
  nothing left.
- **Not working:** the meaning shifted, or the text got shorter but lost a
  domain-specific fact or number it needed to stay useful.

## Where it fits

Applies by default to prose this repo's other skills produce — `wayfinder`'s ticket
write-ups, `prototype`'s hand-off notes — a cross-cutting pass, not tied to one
workflow. See the full [SKILL.md](../../../skills/productivity/unslop/SKILL.md) for
the full pattern list.
