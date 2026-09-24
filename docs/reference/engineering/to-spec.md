# to-spec

## What it does

Turns the current conversation and codebase understanding into a spec and publishes it
to the project issue tracker, labelled `ready-for-agent`. It deliberately does not
interview you; it synthesizes what you've already discussed. It explores the repo to
ground the spec in the codebase's real state, picks the seams the feature will be tested
at, confirms those with you, and writes the spec. It prefers existing seams, the highest
one available, and ideally just one.

The spec has fixed sections: Problem Statement, Solution, an extensive numbered list of
User Stories, Implementation Decisions, Testing Decisions, Out of Scope, and Further
Notes. It avoids file paths and code snippets because they go stale. The one exception
is a prototype snippet that encodes a decision more precisely than prose can, such as a
state machine, reducer, schema, or type shape.

## When to reach for it

After a grilling or design conversation, when the thinking is done and you want it
captured as a durable spec on the tracker. It's a synthesis step, not a discovery step.

## FAQ

**Should I run this before or after grilling?**
After. `to-spec` has no interview mode. If the plan is still fuzzy, run `grilling` or
`grill-with-docs` first, then synthesize.

**Where does the spec live?**
As an issue on the configured tracker, labelled `ready-for-agent`. `setup-skills`
decides which tracker that is.

**Why such a long user-story list?**
Coverage. Forcing an exhaustive list surfaces aspects of the feature that a short one
glosses over.

## Signals

- **Working:** you read the published spec and it matches what you discussed, needing
  only edits.
- **Not working:** it starts asking you questions, or the Implementation Decisions
  section is full of file paths and snippets.

## Where it fits

Depends on the tracker config from `setup-skills`. Grilling skills feed it, and
`to-tickets` splits its output into executable tickets. See the full
[SKILL.md](../../../skills/engineering/to-spec/SKILL.md).
