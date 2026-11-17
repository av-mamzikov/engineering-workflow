---
name: engineering-workflow
description: Combine project OpenSpec guidance with Compound Engineering skills for non-trivial engineering work, from requirements and planning through implementation and independent review. Also supports projects without OpenSpec using their existing requirements and plans.
---

# Engineering workflow

Apply the user's engineering conventions while using existing specialist skills. Read each applicable installed skill's `SKILL.md` in full before applying it. Discover dependencies by skill name in the current environment; do not rely on machine-specific paths or modify installed third-party skills.

## Check project dependencies when needed

Use `engineering-setup` before the first OpenSpec or Graphify operation in the target project, and recheck if the project or dependency state changes. Check only the dependency needed for that operation; do not make unrelated work wait for unused project tools. Reuse verified readiness within the current task while it remains applicable.

The set installer checks the Compound Engineering plugin, including user-level availability. If it later becomes unavailable, route the dependency problem through `engineering-setup`. Do not initialize OpenSpec merely because the skill set is installed or invoked.

## Select the necessary work

Use only relevant stages and reuse agreed plans:

| Task | Installed skill |
| --- | --- |
| Explore requirements | `ce-brainstorm` |
| Plan work | `ce-plan` |
| Review requirements, specifications, or plans | `engineering-spec-review`, using `ce-doc-review` |
| Implement agreed work | `ce-work` |
| Investigate a bug | `ce-debug` |
| Review any implementation that changes code | `engineering-code-review`, using `ce-code-review` |
| Relevant browser checks | `ce-test-browser` |

The companion skills are part of this set and must also be installed. If a required dependency is missing, identify it and report which work is affected. Continue independent authorized work, but do not silently substitute a self-review for required independent review or declare affected work complete.

Verify behavior with appropriate tests and acceptance scenarios. Report actual results and material limitations. Even a small code change requires the independent review specified by `engineering-code-review`; the non-trivial-work threshold does not exempt it. When document review findings are corrected, follow the independent re-review loop in `engineering-spec-review`.

## OpenSpec projects

Also use available OpenSpec skills. After the project readiness check through `engineering-setup`, first read `openspec/README.md`, relevant specifications, and current change documents when present. Follow the project's documented change workflow, approved requirements, and acceptance scenarios. Distinguish proposals from agreed decisions.

Use OpenSpec for the project's specification and change structure, and Compound Engineering for the relevant work procedures. Pass the governing requirements, current change documents, and agreed plans into each selected CE stage. CE brainstorming and planning must respect the project's approval state; they do not turn a proposal into an approved requirement.

When working within an existing OpenSpec change, keep plans and verification evidence in that change structure. Avoid duplicate specifications and plans. Missing project guidance or unresolved approval status must be reported when it prevents correct work; do not invent approvals or exceptions.

If a CE skill's default artifact location would create a parallel plan or specification, use the project's existing change structure for the authorized work. If the project workflow and a required skill cannot be reconciled within that scope, report the conflict instead of silently bypassing either requirement. Do not initialize OpenSpec merely to run this set; in projects without OpenSpec, use the existing project requirements and plans with the same verification and review rules.

## Delegate with clear boundaries

Delegate other tasks according to complexity only when the work can be clearly separated and its result independently verified. Useful scopes include requirements and plan review, code relationships and existing components with file references, acceptance scenarios and edge cases, distinct debugging hypotheses, and independent implementation with no concurrent edits to the same files.

Give each subagent a specific scope, relevant context, constraints, and expected deliverables. The main agent evaluates results, integrates changes, and verifies the final outcome. Required code reviews and document re-reviews must use a separate subagent as their companion skills specify.

Continue autonomously within authorized scope. These workflows do not expand authorization for commits, pushes, publishing, or other external actions. If a dependency skill includes a shipping stage, perform it only when already authorized by the user.
