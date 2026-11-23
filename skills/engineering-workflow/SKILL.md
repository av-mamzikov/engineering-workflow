---
name: engineering-workflow
description: Coordinate OpenSpec and Compound Engineering from creating or changing requirements through planning, implementation, independent review, and completion. Also supports projects without OpenSpec.
---

# Engineering workflow

Apply the user's engineering conventions while using existing specialist skills. Read each applicable installed skill's `SKILL.md` in full before applying it. Discover dependencies by skill name in the current environment; do not rely on machine-specific paths or modify installed third-party skills.

## Check project dependencies when needed

Use `engineering-setup` before the first OpenSpec or Graphify operation in the target project, and recheck if the project or dependency state changes. Check only what the operation needs. Reuse the result for the rest of the task while it remains valid.

The set installer checks the Compound Engineering plugin, including user-level availability. If it later becomes unavailable, route the dependency problem through `engineering-setup`. Do not initialize OpenSpec merely because the skill set is installed or invoked.

## Select the necessary work

Use only relevant stages and reuse agreed plans:

| Task | Installed skill |
| --- | --- |
| Create initial requirements or change existing requirements | `engineering-requirements`, with `ce-brainstorm` for exploration |
| Plan work | `ce-plan` |
| Review requirements, specifications, or plans | `engineering-spec-review`, using `ce-doc-review` |
| Implement agreed work | `ce-work` |
| Investigate a bug | `ce-debug` |
| Review any implementation that changes code | `engineering-code-review`, using `ce-code-review` |
| Relevant browser checks | `ce-test-browser` |

Route an idea or change request that needs requirements to `engineering-requirements`. For a requirements-only request, return its reviewed documents, approval status, and blockers. When planning is also in scope, give `ce-plan` the canonical requirements paths, decisions, and open questions. Follow the project's approval rules and plan only the scope ready for planning. If suitable requirements already exist, use them directly.

The companion skills are part of this set and must also be installed. If a required dependency is missing, identify it and report which work is affected. Continue independent authorized work, but do not silently substitute a self-review for required independent review or declare affected work complete.

Use `engineering-code-review` for every code change, including small fixes. When document review findings are corrected, follow the independent re-review loop in `engineering-spec-review`.

## Verify changes before completion

During implementation and after fixes, run tests for the affected behavior and check the applicable acceptance scenarios. Before declaring a code change complete, run the project's full test suite on the final changed state. Use the full suite of an affected independent component instead only when the project has an established verification boundary for that component and the change stays within it. Apply this completion requirement regardless of the selected skill or execution mode, including when `ce-work` returns implementation to a caller; the main agent owns final verification.

If the required full run cannot be completed, report why, which checks ran and their results, and the remaining verification gap. Passing selected tests does not establish that the full suite passed; do not declare verification complete while required checks remain unrun or failing.

For documentation-only changes, run the applicable documentation checks. Report actual results and material limitations.

## Complete or hand off work

When the user asks to solve or complete a task autonomously, the main agent owns the requested outcome and continues in the same turn through every applicable, authorized step. Respect any narrower endpoint the user specifies. A specialist's standalone completion message is a progress update in this workflow. When `openspec-apply-change` reports that all tracked tasks are complete, run any remaining checks, then invoke `openspec-archive-change` with the exact name of that change once it is ready. Reuse verification evidence that still covers the current state. On resumption, inspect the current state before repeating a completed step.

An agreed OpenSpec change is ready for local closure when its required artifacts and tasks are complete, acceptance and final checks have passed, and independent review has no unresolved serious findings. Follow the project's closure rules. Assess the delta specs and show the sync summary as a progress update. Pass the user's autonomous completion request to the archive skill as their existing choice of **Sync now** when agreed delta specs need merging, or **Archive now** when they are already synced. If there are no delta specs, proceed directly to archive. Verify the sync when applicable, then verify the archived change before giving the final report.

Continue without a routine handoff or repeated confirmation when the next step is already authorized. If the change cannot be identified, its required sync fails or is blocked, or closure requires an unresolved decision or approval, finish all independent work and report the specific blocker and pending step.

In an assisted task, the user can retain the readiness decision. Give them the completed checks, any remaining gaps, and the proposed OpenSpec closure steps. When the readiness decision is theirs, stop before syncing or archiving and wait for their decision. If they already approved those steps, continue within that approval.

## OpenSpec projects

Also use available OpenSpec skills. After the project readiness check through `engineering-setup`, first read `openspec/README.md`, relevant specifications, and current change documents when present. Follow the project's documented change workflow, approved requirements, and acceptance scenarios. Distinguish proposals from agreed decisions.

Use OpenSpec for the project's specification and change structure, and Compound Engineering for the relevant work procedures. Pass the governing requirements, current change documents, and agreed plans into each selected CE stage. CE brainstorming and planning must respect the project's approval state; they do not turn a proposal into an approved requirement.

When working within an existing OpenSpec change, keep plans and verification evidence in that change structure. Avoid duplicate specifications and plans. Missing project guidance or unresolved approval status must be reported when it prevents correct work; do not invent approvals or exceptions.

If a CE skill's default artifact location would create a parallel plan or specification, use the project's existing change structure for the authorized work. If the project workflow and a required skill cannot be reconciled within that scope, report the conflict instead of silently bypassing either requirement. Do not initialize OpenSpec merely to run this set; in projects without OpenSpec, use the existing project requirements and plans with the same verification and review rules.

## Delegate with clear boundaries

Delegate other tasks according to complexity only when the work can be clearly separated and its result independently verified. Useful scopes include requirements and plan review, code relationships and existing components with file references, acceptance scenarios and edge cases, distinct debugging hypotheses, and independent implementation with no concurrent edits to the same files.

Give each subagent a specific scope, relevant context, constraints, and expected deliverables. The main agent evaluates results, integrates changes, and verifies the final outcome. Required code reviews and document re-reviews must use a separate subagent as their companion skills specify.

Continue autonomously within authorized scope. These workflows do not expand authorization for commits, pushes, publishing, or other external actions. If a dependency skill includes a shipping stage, perform it only when already authorized by the user.
