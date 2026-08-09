### Scaffolding from new

**Use when:** the task is starting a new project, package, or service from nothing.

> Stub — flesh out with the actual steps you follow once this has been used a few times. Placeholder shape below.

1. Name the destination — what "done" looks like for the first slice — before writing any files. If the scope is large enough to span multiple sessions, chart it with `wayfinder` instead of starting to build.
2. Settle the foundational structure (language/framework, layout, tooling) as a short list of decisions, not by writing code first.
3. Scaffold the skeleton: directories, config, one trivial end-to-end path proven working before building on top of it.
4. Layer in real functionality slice by slice, keeping each slice runnable.
5. Set up whatever verification loop the project will live by (tests, typecheck, CI) as part of the scaffold, not as an afterthought.
