---
name: engineering-spec-review
description: Review engineering proposals, requirements, designs, and implementation plans against governing requirements and approved decisions using ce-doc-review. Require independent subagent re-review after corrections.
---

# Specification and plan review

Use the installed `ce-doc-review` skill where applicable and read its `SKILL.md` in full. Apply to proposals, requirements, specifications, designs, and plans. Before using OpenSpec, check the project with `engineering-setup` or reuse a still-valid check from this task. Then read `openspec/README.md`, relevant specifications, and current change documents, and use available OpenSpec skills. Keep plans and verification evidence inside the existing change structure; avoid duplicate specifications and plans. Projects without OpenSpec use their existing requirements and plans; do not initialize it for a review.

## Establish governing sources

Give reviewers readable paths to the documents being reviewed, applicable main specifications, general requirements, project guidance, and evidence of approved decisions. Require them to read these sources, not just a summary of the proposed changes. Distinguish proposals from agreed requirements and acceptance scenarios.

Check specific scenarios and exceptions against the general requirements. Report contradictions with references to both conflicting statements. Require explicit evidence that the exception was approved. If a governing source or approval evidence cannot be found, report the gap and its effect rather than inventing an exception.

For an OpenSpec change, use the same review and correction process for each artifact.

- **Proposal and capability deltas.** Check that the acceptance scenarios cover the proposed outcome and boundaries, including relevant exceptions and compatibility guarantees. Surface unresolved product decisions for the decision owner.
- **Design.** Trace the affected UI states, API behavior, and architectural choices to the approved scenarios and project conventions. Identify any design decision that changes an agreed requirement.
- **Implementation plan.** Check that every agreed scenario and material design decision is covered by a task or verification step, prerequisites precede dependent work, and tasks stay within scope. Check migration and compatibility work when the approved design calls for it.

Report the review verdict separately from approval. In `engineering-change-planning`, the user approves reviewed requirements and design in interactive mode. In autonomous mode, the coordinator may approve decisions within the user's delegation. Attribute each approval to its actual owner. The plan review establishes readiness for the handoff requested by the caller.

## Evaluate findings and correct documents

Ask the independent reviewer to identify errors and omissions, cite the relevant passages, and explain their consequences. The main agent coordinates the review. In autonomous mode, it decides which findings to accept or reject within the authorized scope and applies the accepted corrections without asking the user to triage them. Record the basis for disputed decisions and reopen rejected findings only when new evidence warrants it. If a correction would change a user-approved requirement or design decision, return that decision to the user. Keep decisions and verification evidence with the reviewed artifact in the project's existing structure.

## Independent re-review after corrections

After fixing document review findings, including findings in requirements, specifications, and plans, have a separate subagent review the updated documents again using `ce-doc-review` where applicable. Give the reviewer the updated documents and paths to the governing sources. Require them to read both again. You may use the same reviewer if they are independent of the editing agent.

Evaluate the new findings, fix substantiated issues, and repeat corrections and independent review until no substantiated serious findings remain. Minor recommendations do not block completion.

If repeated reviews make no meaningful progress, or resolving a serious finding requires additional authorization or a user decision, report the blocker and unresolved serious findings. Do not repeat unchanged cycles or declare the work complete. If a required skill or separate reviewer is unavailable, report the limitation and remaining review requirement; continue only independent authorized work.

Report the documents and governing sources reviewed, review coverage, actual corrections and checks, unresolved decisions, remaining serious findings or minor recommendations, and material limitations. Review does not authorize commits, pushes, publishing, or other external actions.
