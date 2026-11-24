---
name: engineering-change-planning
description: Design an OpenSpec change from its proposal through reviewed requirements, UI, API, and architectural decisions to a reviewed implementation plan. Use for “спроектируй изменение”, a request to prepare a complete OpenSpec change, or the planning phase of engineering-workflow.
---

# OpenSpec change planning

Produce a reviewed implementation plan in the change directory. A request limited to requirements uses `engineering-requirements` and ends after stage 2. Standalone change planning ends after stage 6. For a full-cycle task, return the plan to `engineering-workflow` for the pre-implementation commit.

## Establish the change and decision owner

Use `engineering-setup` before the first OpenSpec operation, or reuse the current task's readiness check. Read the project's instructions, `openspec/README.md` when present, governing specifications, and the existing change. Follow the branch-selection rules in `engineering-requirements` before the first write. Reuse the matching change and its artifacts. The names below follow the standard schema. Use the project's equivalents and select individual artifact instructions if a bulk command would also create later artifacts.

Carry the caller's mode, scope, and any decisions the user reserved into every specialist handoff. Standalone planning is interactive unless the user delegates planning decisions. In interactive mode, ask the user the material questions and obtain their approval of the reviewed requirements and then of the reviewed design. In autonomous mode, the coordinator can make and approve in-scope choices after independent review. Record who decided, what they approved, and why. Ask the user before changing an explicit condition or deciding outside the delegation. Honor project rules that reserve approval for a specific person.

## Six stages

1. **Draft the proposal.** Use `engineering-requirements` for stages 1 and 2. Capture the problem, outcome, scope, and affected capabilities in `proposal.md`.
2. **Review the proposal and agree on requirements.** Write the capability deltas and acceptance scenarios in `specs/`. Review them together with the proposal using `engineering-spec-review`. Resolve serious findings and obtain the decision owner's approval of the reviewed requirements before design.
3. **Develop the design.** Record the solution in `design.md`. For UI changes, show the user flow and important states, with a sketch for a new interaction or a reference to the established pattern. For API changes, show representative requests, responses, errors, and compatibility implications. Explain architectural choices through the affected components and relevant trade-offs. Briefly identify unaffected areas.
4. **Review and agree on the design.** Run `engineering-spec-review` against the approved requirements. Resolve serious findings and obtain the decision owner's approval of the affected UI, API, and architecture. If the design changes an agreed requirement, return to stage 2 for review and approval of the revision.
5. **Write the implementation plan.** After design approval, apply `ce-plan`'s research, task breakdown, and verification guidance to the approved requirements and design. The coordinator writes the canonical `tasks.md` using the OpenSpec change's location, schema, and task format. If CE's standalone writer requires a separate plan, use its planning guidance directly and write only the OpenSpec artifact. Order tasks by dependency and include the checks that demonstrate the acceptance scenarios.
6. **Review the implementation plan.** Use `engineering-spec-review` to check `tasks.md` against the approved requirements and design. Resolve substantiated findings and have corrections independently re-reviewed. Run the project's OpenSpec validation on the resulting change. Report readiness, artifact paths, approvals, review outcomes, and any blockers.

Keep decisions and review evidence with the change. On resumption, reuse approvals and reviews that still cover the current artifacts. Resume at the earliest unmet stage, even if later files already exist. When a decision changes, repeat affected reviews and approvals before relying on downstream artifacts. A missing required approval, failed validation, or unresolved serious finding keeps the affected work pending.
