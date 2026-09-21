# clean-copy

## What it does

Cuts interface copy that shouldn't exist — captions that restate a label, hints that
pre-empt a worry the user never had, warnings that are scar tissue from a fixed bug.
Walks each string down a ladder (does it need to surface at all → does the label need
to exist → is it pre-empting something the user never had to consider → rewrite or
delete) and stops at the first rung that fires. Copy survives only when the user
genuinely cannot act without it: a real consequence at the moment of choosing, a
compatibility fact they can't see, what a blank state means, or units on a bare value.

## When to reach for it

Model-invoked — it fires when writing or reviewing any user-facing string (labels,
hints, empty states, toasts, confirmations, button text), or when asked to clean up or
tighten copy. When reviewing a batch, it reports as `file:line` with the current
string and either a rewrite or `cut`, and names which rung failed; it doesn't rewrite
copy that already passes.

## Where it fits

Experimental, so its shape may still change. Adjacent to `unslop` (cuts AI tells from
prose) but scoped to interface copy specifically, where the question is less "does
this read well" and more "should this string exist at all." See the full
[SKILL.md](../../../skills/experimental/clean-copy/SKILL.md).
