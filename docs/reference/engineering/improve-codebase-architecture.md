# improve-codebase-architecture

## What it does

Surveys a codebase for **deepening opportunities**, refactors that turn shallow modules
into deep ones, and presents them in a self-contained HTML report so you can see the
trade-offs instead of reading an abstract list. It scopes the scan with YAGNI: recent
commit history points at the hot spots worth deepening, so it looks where change
actually happens.

It reads `CONTEXT.md` and relevant ADRs first, then spawns a sub-agent to walk the code
and note friction: concepts that require bouncing between small modules, interfaces
nearly as complex as their implementations, pure functions extracted only for
testability, and modules leaking across seams. Each candidate gets a before/after
visualization and a recommendation strength badge, and the report ends with a ranked top
recommendation. You pick one, and it grills through the decision with `grilling` while
`domain-modeling` keeps the domain model current. It offers an ADR when a rejection is
load-bearing, and uses design-it-twice from `codebase-design` to explore alternative
interfaces.

## When to reach for it

Periodically, as an architecture survey rather than a rescue. It finds the candidates;
it doesn't untangle the mud for you. It's also useful when a specific area feels painful
and you want the friction named.

## FAQ

**Does it change any code?**
No. It produces a report and then a grilling conversation. Any code change is a later,
separate decision.

**Where does the report go?**
The OS temp directory, at `<tmpdir>/architecture-review-<timestamp>.html`, and it opens
in your browser. Nothing lands in the repo.

**Why its own vocabulary?**
It uses `codebase-design`'s terms exactly: module, interface, depth, seam, adapter,
leverage, locality. It avoids "component", "service", "API", and "boundary", which are
overloaded enough to blur the design discussion.

**What about an ADR it seems to contradict?**
It surfaces the conflict only when the friction is real enough to justify revisiting the
ADR, and marks it clearly. It does not list every theoretical refactor an ADR forbids.

## Signals

- **Working:** a short list of strong, concrete candidates, each with a before/after
  that makes the shallowness obvious.
- **Not working:** a long list of theoretical refactors, or candidates that ignore the
  project's existing domain language.

## Where it fits

Builds on the model-invoked `codebase-design` and drives `grilling` and `domain-modeling`
once you pick a candidate. `wayfinder` can file a prototype or research ticket before
the decision. See the full
[SKILL.md](../../../skills/engineering/improve-codebase-architecture/SKILL.md).
