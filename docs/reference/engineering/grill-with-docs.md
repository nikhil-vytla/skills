# grill-with-docs

## What it does

The same round-based interview as `grill-me`, pointed at a codebase and stateful: as
terms resolve they land in a `CONTEXT.md` glossary the moment they resolve, and
decisions that clear all three ADR gates (hard to reverse, surprising without context,
a real trade-off) land in `docs/adr/`. Both files are created lazily — nothing is
scaffolded up front. It runs `grilling` for the interview and `domain-modeling` for the
writing.

## When to reach for it

At the start of a change, in a repo, when the plan is fuzzy and the words for the thing
aren't settled. Type `/grill-with-docs` explicitly — it never fires on its own. It also
works aimed at a repo rather than a change ("help me document my repo"). Scope decides
between this and `wayfinder`: this for anything you can settle in one session,
`wayfinder` when the effort needs charting as decision tickets first. With no repo at
all, use `grill-me`.

## FAQ

**It ran but no CONTEXT.md or ADRs appeared — broken?**
Often not: ADRs need all three gates and most sessions produce none, and a session with
no new vocabulary has nothing to write. But if the interview also arrived as one big
question dump with no recommendations, the model skipped loading `grilling` or
`domain-modeling` — ask it directly which skills it loaded.

**Where do the decisions that don't become ADRs go?**
Into the conversation only. The glossary is deliberately not a spec, so hand the same
conversation onward rather than clearing it and assuming the files captured everything.

## Signals

- **Working:** `CONTEXT.md` changes during the session term by term, reads as pure
  vocabulary, and questions the codebase can answer get answered by reading it, not
  asked of you.
- **Not working:** the glossary fills with implementation detail and spec-like prose,
  or every decision gets an ADR.

## Where it fits

A one-line wrapper needing both `grilling` and `domain-modeling` installed — alone it
doesn't work. Stateful sibling of `grill-me`; `wayfinder` sits upstream for
multi-session efforts and can hand parts of its map back down to it. See the full
[SKILL.md](../../../skills/engineering/grill-with-docs/SKILL.md).
