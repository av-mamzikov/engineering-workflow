## Engineering workflow

Use `engineering-requirements` for requirements alone and `engineering-change-planning` to design an OpenSpec change through a reviewed implementation plan. Stop at the requested endpoint. Use `engineering-workflow` for the full cycle. Interactive planning asks the user to approve requirements and design. An autonomous request delegates those in-scope decisions to the coordinator, subject to explicit constraints and project approval rules.

For non-trivial engineering work, use `engineering-workflow` and applicable installed Compound Engineering skills by default. Read each relevant `SKILL.md` in full before applying it. Use `engineering-spec-review` for requirements, specification, and plan reviews, including independent re-review after corrections. After any implementation that changes code, including small changes, use `engineering-code-review`: independent subagent review and re-review after fixes are mandatory. If a required skill or reviewer is unavailable, report the limitation; do not silently waive required review or declare the affected work complete.

Before using OpenSpec or Graphify in a project, use `engineering-setup` to check and prepare the dependency needed for that operation. Reuse a still-valid readiness check from the current task. Installing this skill set does not initialize those tools in projects.

## Git branch naming

Use the branch name the user requests. Otherwise, take the task or issue ID from the request, current task, or plan. Preserve its spelling and case. Use the ID alone by default (e.g. `FPP-6315`), or `FPP-6315-short-description` when useful. Never invent an ID. Do not prepend `codex/`, `feat/`, `fix/`, or another prefix unless the user explicitly requests it. If no branch name was explicitly provided and the ID is missing or ambiguous, ask before creating a branch. Do not rename existing branches unless requested.

## UI conventions

Before adding or changing a UI element, inspect equivalents in the same form, then other project forms if needed. Reuse existing components, styles, label placement, spacing, and interaction patterns.

## Graphify

When the user requests `$graphify`, read and follow the installed Graphify skill before other work; if missing, use `engineering-setup` to prepare it first. Check project readiness through `engineering-setup` before Graphify operations. A graph can be built with `graphify .`. For codebase questions, if the target repository contains `graphify-out/graph.json`, first run `graphify query "<question>"`; use `graphify path "<A>" "<B>"` for relationships and `graphify explain "<concept>"` for focused concepts. Read `graphify-out/GRAPH_REPORT.md` only for broad architecture review or insufficient query results. With Graphify hooks installed, post-commit and post-checkout refresh the local AST graph in the background. Do not run `graphify update .` after edits; the graph may lag behind uncommitted changes or a running rebuild.

## Authorization

An explicit full-cycle OpenSpec request includes a local commit of the reviewed change before implementation and a final local commit after verification, sync, and archive. Honor narrower instructions. Pushes, publication, and other external actions require separate authorization.
