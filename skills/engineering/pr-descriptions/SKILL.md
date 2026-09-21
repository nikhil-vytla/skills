---
name: pr-descriptions
description: Write high-signal pull request descriptions with mermaid diagrams, real code snippets, and PR-train conventions. Use when drafting or improving PR bodies, especially for stacked PR trains in large repos. Ships a reusable PR_TEMPLATE.md for repos where a checked-in template is not an option.
---

# PR descriptions

A PR description is the one artifact every reviewer reads before the diff. Its job: let a reviewer predict what they will see in the diff, and judge the change without reverse-engineering intent from code. Everything below serves that.

## Core structure

Four sections, in this order. Omit a section only when it would be empty, never because it is hard to write.

1. **Problem** — the need, written for someone outside the immediate work. State what is missing or broken and why it matters, without mentioning the solution. If the reader would ask "why now?", answer it here.
2. **Solution** — what changed, as bullets. One bullet per idea, each anchored to a file or symbol in backticks. Inline a short code snippet under the bullet when the key API or shape says it better than prose.
3. **Architecture** (or a content-specific heading like "How a score is built", "Run pipeline", "Shape") — one diagram and/or one exemplar snippet. See the diagram and snippet rules below.
4. **Testing** — the exact command, then what the tests *pin* (invariants, counts, regressions), not adjectives. "31 tests: dimension counts pinned exactly, weights sum to 100" beats "well tested". Include real output tables for E2E runs.

## Diagrams (mermaid)

GitHub renders ` ```mermaid ` fences natively — prefer them over image attachments: they diff, they survive repo moves, and they cost nothing to update.

Choose the diagram type by what the reviewer must hold in their head:

| Content | Type |
| --- | --- |
| Data contracts, record/model relationships | `classDiagram` |
| Runtime protocol, call ordering, loops per item | `sequenceDiagram` |
| Pipelines, composition, provenance, dataflow | `flowchart LR` / `flowchart TD` |

Rules that keep mermaid rendering on GitHub:

- Quote every node label: `A["load_bundle"]`. Unquoted parentheses, commas, and angle brackets break the parser.
- Line-break inside labels with `<br/>`.
- Keep node ids short and alphanumeric; put the real names in the label.
- Edge annotations: `-- label -->` for solid, `-. label .->` for dotted (good for "warning path", "drift test").
- One diagram per PR, maximum. Diagram the one structure the diff is about — not the whole system (save that for the combined/final PR).
- `Note over X: ...` in sequence diagrams is the place for cross-cutting facts (e.g. "blinded — system_id is type-unreachable").

## Code snippets

- **Real over invented**: paste from the diff, the resources, or actual output — then trim. A trimmed real preset teaches more than a schematic one.
- Show the **API or data shape**, not the implementation. A reviewer needs the call site and the row format; the implementation is the diff itself.
- Trim aggressively with `...` and keep snippets under ~15 lines.
- Annotate inline with comments or `<- arrows` for the one thing to notice: `models: [- *gemini_flash]  # add a second anchor here -> judge panel`.
- Real output (CSV rows, leaderboard excerpts, error messages) is the strongest possible evidence in a Testing section.

## Callouts

Use GitHub alert syntax for meta-context — things about *reviewing the PR*, not about the code:

```markdown
> [!NOTE]
> Large by line count but entirely static markdown snapshots — reviewing this PR is spot-checking transcription fidelity, not reading code.
```

Good uses: not-for-merge branches, review-cost guidance ("mostly generated/static"), separability notes ("this carriage could move to its own ticket"). One per PR, at most two.

## PR-train specifics

- **TOC in every PR body**, wrapped in `<pr-train-toc>...</pr-train-toc>`, with a pointer (👉/👈) on the current PR. Update every body when the train changes shape.
- **Position narrative**: one sentence on where the PR sits and why — "Sits between the scorers (#N) and the wiring (#N+2) so the import in `_registry` resolves; earlier carriages don't import it."
- **Each PR must be CI-green standalone**; say so in Testing with the per-branch test count.
- **No cross-PR churn**: author every file once, in its final form, in the PR that owns it. If a later PR rewrites an earlier PR's file, the boundary is wrong — move the content, don't document the churn.
- **Size**: target 250–500 changed lines. Static transcriptions/snapshots/generated files may exceed it if the body says so with a callout. Split at genuine seams (a module whose tests import nothing else is a seam).
- **Combined branch**: not for review, not for merge — say it in a callout. This is the home for the whole-system architecture diagram and E2E results tables.
- **File tables with SHA-pinned permalinks** (`https://github.com/org/repo/blob/<sha>/path`) when the file set is non-obvious; reference-style links keep the table readable.

## Anti-patterns

- Restating the diff in prose ("added function X that does Y" for every function).
- Adjectives as evidence ("thoroughly tested", "significantly faster") — give the command, the count, the number.
- A diagram of the entire system on a 300-line PR.
- Screenshots of code or terminal output — paste the text.
- Describing what reviewers can see instead of what they cannot: intent, constraints, rejected alternatives, and where the bodies say "why", commit messages and PR bodies are the correct home for cross-project context that does not belong in code comments.

## Naming

- **PR title**: `[JIRA-XXX] Short description of changes` — the ticket key up front so it's greppable in PR lists and release notes.
- **Branch name**: `<username>-YYYYMMDD-camelCaseDescription` — e.g. `nikhil-20260920-fixScorerDrift`.
- **JIRA link**: every PR body ends with a `---` divider followed by `JIRA: <link-to-jira-ticket>` (see `PR_TEMPLATE.md`).

## Template

`PR_TEMPLATE.md` in this skill directory is the fill-in skeleton. Use it directly in repos where a checked-in `.github/PULL_REQUEST_TEMPLATE.md` is not an option (e.g. a monorepo you don't own): copy it into the PR body and fill it in, or point this skill at it when drafting.
