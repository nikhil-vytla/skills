# pr-descriptions

## What it does

Writes high-signal PR descriptions structured as Problem → Solution → Architecture (or
a content-specific heading) → Testing, so a reviewer can predict the diff and judge the
change without reverse-engineering intent. Covers mermaid diagram choice and syntax
rules that keep GitHub rendering intact, real-over-invented code snippets trimmed to
the API or data shape, GitHub alert-style callouts for review meta-context, and
PR-train conventions (TOC, position narrative, per-branch CI-green, no cross-PR churn,
SHA-pinned file tables). It also fixes naming: `[JIRA-XXX] Short description` for
titles, `<username>-YYYYMMDD-camelCaseDescription` for branches, and a trailing `JIRA:`
footer. Ships a standalone `PR_TEMPLATE.md` for repos where a checked-in
`.github/PULL_REQUEST_TEMPLATE.md` isn't an option.

## When to reach for it

Model-invoked, so it fires when drafting or improving a PR body, especially for stacked
PR trains in large repos. Reach for `PR_TEMPLATE.md` directly by copying it into the PR
body when a repo has no checked-in template of its own.

## Where it fits

Standalone. Complements `wayfinder`'s ticket-charting once a ticket is ready to ship as
a PR, and follows `unslop`'s writing-cleanup pass for the resulting prose. See the full
[SKILL.md](../../../skills/engineering/pr-descriptions/SKILL.md).
