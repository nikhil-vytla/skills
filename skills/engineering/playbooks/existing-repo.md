### Working in an existing repo

**Use when:** the task is a change, fix, or feature inside a codebase that already has established conventions, tests, and history.

> Stub — flesh out with the actual steps you follow once this has been used a few times. Placeholder shape below.

1. Orient. Read `AGENTS.md`/`CLAUDE.md` and any repo-local skill or doc conventions before touching code. Find the existing pattern for what's being changed rather than inventing a new one.
2. Reproduce or confirm the current behavior before changing it, if the task is a fix.
3. Make the change as the smallest coherent diff that satisfies the task. Reach for `prototype` first if the shape of the change is genuinely in question.
4. Verify against the repo's real checks (tests, typecheck, lint, running the app) — not just "it compiles".
5. Run `unslop` on any prose (PR description, commit message, comments) before handing back.
