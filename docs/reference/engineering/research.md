# research

## What it does

Spins up a background agent to answer a question, so you keep working while it reads.
The agent investigates against **primary sources**: official docs, source code, specs,
first-party APIs. It follows every claim back to the source that owns it rather than
trusting a secondary write-up. It writes the findings to a single Markdown file, citing
each claim's source, and saves it where the repo already keeps such notes. It matches
the existing convention, or picks a sensible location and names it if there is none.

## When to reach for it

When you need a topic researched, docs or API facts gathered, or reading legwork
delegated. Model-invoked, so it can fire when a task needs grounding in external facts.

## FAQ

**Primary vs secondary sources?**
Primary means the thing that owns the claim: the official docs, the source code, the
spec. A blog post explaining the API is secondary and doesn't count as the citation.

**Where does the findings file go?**
Wherever the repo already keeps research notes. With no convention, it picks a sensible
place and tells you where.

**Does it block my work?**
No. It runs as a background agent so you can continue.

## Signals

- **Working:** every claim in the output traces to a primary source, and the file lands
  where the repo's other notes live.
- **Not working:** it summarizes secondary explainers, or the write-up has uncited claims.

## Where it fits

`wayfinder` files "research" as one of its four ticket types and resolves those tickets
with this skill. Findings can feed `to-spec` or a `grilling` session. See the full
[SKILL.md](../../../skills/engineering/research/SKILL.md).
