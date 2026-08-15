# show-me

## What it does

Explains the current topic of conversation visually instead of in prose: pseudocode
for logic, call trees for runtime flow, component trees for UI structure, shallow file
trees for responsibilities, Mermaid for interactions, diffs when the point is what
changes, and — for anything too dense for those — one focused HTML file opened in the
browser. It picks the smallest view that makes the key point clear and keeps the
surrounding text brief.

## When to reach for it

It's model-invoked — it fires when a visual would land better than a paragraph — but
typing `/show-me` works whenever an explanation isn't clicking: an architecture you're
trying to hold in your head, a refactor's before/after shape, a control flow buried in
prose. It renders the current conversation topic, so use it mid-discussion rather than
as a standalone generator.

## FAQ

**How is this different from `prototype`?**
Direction. `prototype` builds a throwaway artifact to *answer a design question you
haven't decided yet*; `show-me` illustrates *what's already being discussed* so both
sides are looking at the same picture. One produces evidence, the other produces
understanding.

**Which of its formats should I expect?**
Whichever is smallest for the point — usually one, sometimes a few, never all. Diffs
when something changes shape, trees when structure is the point, Mermaid when actors
interact, HTML only when the concept is too dense for text-shaped views.

## Signals

- **Working:** each visual sits next to one short piece of text, contains only the
  calls/files/states needed for the current question, and the smallest format won.
- **Not working:** every reply sprouts a wall of diagrams, or an HTML artifact appears
  for something a five-line tree would have shown.

## Where it fits

A conversation-level aid like `bro` (which restates in plain language; this one
restates in pictures). Pairs naturally with grilling sessions when a question needs a
structure on the table before it can be answered. See the full
[SKILL.md](../../../skills/productivity/show-me/SKILL.md).
