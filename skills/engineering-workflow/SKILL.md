---
name: engineering-workflow
description: Run an engineering task end to end in interactive or autonomous mode. For OpenSpec, coordinate change planning, a planning commit, implementation and verification, sync and archive, and the final local commit. Also supports projects without OpenSpec.
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
| Design an OpenSpec change through a reviewed implementation plan | `engineering-change-planning` |
| Plan work in other projects | Use `ce-plan` for the simplest change that meets current requirements and project constraints. Prefer existing patterns and include the work needed to deliver and verify the change. |
| Review a proposal, specifications, design, or implementation plan | `engineering-spec-review`, using `ce-doc-review` |
| Implement agreed work | `ce-work` |
| Investigate a bug | `ce-debug` |
| Review any implementation that changes code | `engineering-code-review`, using `ce-code-review` |
| Relevant browser checks | `ce-test-browser` |

For “проработай требования”, use `engineering-requirements` and stop with reviewed requirements and their approval status. For “спроектируй изменение”, use `engineering-change-planning` and stop with its reviewed plan. For an end-to-end OpenSpec task, follow the full cycle below. In projects without OpenSpec, use the project's existing requirements and plan, implementation, and review procedures. OpenSpec adoption requires an explicit request.

The companion skills are part of this set and must also be installed. If a required dependency is missing, identify it and report which work is affected. Continue independent authorized work, but do not silently substitute a self-review for required independent review or declare affected work complete.

Use the same review process for proposals, requirements, designs, plans, and code. An independent reviewer reports findings with evidence. The main agent evaluates them, applies substantiated fixes, and submits the revised work for independent re-review. In autonomous mode, the main agent accepts or rejects findings within the approved scope and records the reason for disputed decisions. Follow `engineering-spec-review` for documents and `engineering-code-review` for every code change, including small fixes.

## Choose the operating mode

Use interactive mode unless the user requests autonomous work. Carry the requested endpoint, decision owner, explicit constraints, and permissions into specialist handoffs.

- **Interactive.** Ask the user about material alternatives during planning. Present the reviewed requirements and design for their approval at their respective stages. Reuse explicit decisions that already cover the current version. If the user reserved the closure decision, present verification results and wait for their decision before sync and archive.
- **Autonomous.** A request such as “реализуй задачу автономно” delegates in-scope requirements and design decisions to the coordinator for the full cycle. Make those decisions from the brief, project rules, and independent reviews, and record the decision and its rationale under the coordinator's name. Refer changes to explicit user conditions, choices outside the delegated scope, and approvals reserved for a human back to the user. Continue independent work while a required decision is pending.

A request for the full OpenSpec cycle in either mode authorizes its two local commits, sync, and archive. An explicitly narrower endpoint or Git restriction takes precedence over the sequence below. Requirements-only and planning-only requests end at their handoff unless the user also asks to commit. Pushes, PRs, and publication require their own authorization.

## Full OpenSpec cycle

1. **Design the change.** Hand the scope and mode to `engineering-change-planning`. Use its reviewed, validated change as the input to implementation. Reuse current review and approval evidence for an existing change.
2. **Commit the reviewed change.** Before implementation, make a local commit containing the active change's planning artifacts and associated review evidence. Inspect the commit and retain its SHA. If the exact reviewed change is already committed on the current branch, reuse that commit. When this commit is part of the requested cycle, its failure blocks implementation.
3. **Implement the plan.** Follow the project's OpenSpec apply skill (typically `openspec-apply-change`) in the selected checkout. Use the reviewed tasks and planning commit as inputs. Apply `ce-work`'s implementation and local verification procedures. When its execution mode requires per-unit commits, run those procedures directly under the coordinator and leave edits, tests, and task updates in the worktree. The coordinator owns both commits and closure.
4. **Verify and correct.** Check acceptance scenarios, run the verification below, and obtain independent code review for every code change. Return implementation defects to step 3, rerun affected checks and re-review corrections. If the requirements or design need revision, return to the affected planning stage and revalidate dependent tasks before continuing. Preserve the original planning commit and include the reviewed revisions in the final archived change. Advance only after required checks pass on the final implementation and no substantiated serious findings remain.
5. **Sync and archive.** Confirm that required artifacts and tasks are complete and the project permits closure. Show the delta summary. Use the project's sync and archive procedure for the exact change, verifying applicable deltas in the main specs and the change in its archive. For `openspec-archive-change`, a full-cycle request supplies **Sync now** when deltas need merging or **Archive now** when already synced, subject to any closure decision the user reserved. With no deltas, proceed directly to archive. A failed sync or archive blocks the final commit.
6. **Commit the verified result.** After verifying the archive, commit the implementation, tests, synced specs, and the move from the active change directory to the archive together. Check the commit contents and that all task-owned changes are accounted for. Report the planning and final commit SHAs, archived change path, and verification results.

For both commits, inspect the index and working tree. Include only task-owned changes, including additions and removals, and preserve unrelated staged and unstaged work. On resumption, inspect Git history, implementation state, and the active or archived change. Continue from the first unfinished step with evidence that still matches the current state. If the final commit failed after a successful archive, verify the archive and retry that commit directly.

## Verify changes before completion

During implementation and after fixes, run tests for the affected behavior and check the applicable acceptance scenarios. Before declaring a code change complete, run the project's full test suite on the final changed state. Use the full suite of an affected independent component instead only when the project has an established verification boundary for that component and the change stays within it. Apply this completion requirement regardless of the selected skill or execution mode, including when `ce-work` returns implementation to a caller; the main agent owns final verification.

If the required full run cannot be completed, report why, which checks ran and their results, and the remaining verification gap. Passing selected tests does not establish that the full suite passed; do not declare verification complete while required checks remain unrun or failing.

For documentation-only changes, run the applicable documentation checks. Report actual results and material limitations.

## OpenSpec projects

Also use available OpenSpec skills. After the project readiness check through `engineering-setup`, first read `openspec/README.md`, relevant specifications, and current change documents when present. Follow the project's documented change workflow, approved requirements, and acceptance scenarios. Distinguish proposals from agreed decisions.

Use OpenSpec for the project's specification and change structure, and Compound Engineering for the relevant work procedures. Pass the governing requirements, current change documents, and agreed plans into each selected CE stage. CE brainstorming and planning must respect the project's approval state; they do not turn a proposal into an approved requirement.

When working within an existing OpenSpec change, keep plans and verification evidence in that change structure. Avoid duplicate specifications and plans. Missing project guidance or unresolved approval status must be reported when it prevents correct work; do not invent approvals or exceptions.

If a CE skill's default artifact location would create a parallel plan or specification, use the project's existing change structure for the authorized work. If the project workflow and a required skill cannot be reconciled within that scope, report the conflict instead of silently bypassing either requirement. Do not initialize OpenSpec merely to run this set; in projects without OpenSpec, use the existing project requirements and plans with the same verification and review rules.

## Delegate with clear boundaries

Delegate other tasks according to complexity only when the work can be clearly separated and its result independently verified. Useful scopes include requirements and plan review, code relationships and existing components with file references, acceptance scenarios and edge cases, distinct debugging hypotheses, and independent implementation with no concurrent edits to the same files.

Give each subagent a specific scope, relevant context, constraints, and expected deliverables. The main agent evaluates results, integrates changes, and verifies the final outcome. Required code reviews and document re-reviews must use a separate subagent as their companion skills specify.

Continue autonomously within authorized scope. These workflows do not expand authorization for commits, pushes, publishing, or other external actions. If a dependency skill includes a shipping stage, perform it only when already authorized by the user.
