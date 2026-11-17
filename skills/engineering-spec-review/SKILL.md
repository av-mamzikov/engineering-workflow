---
name: engineering-spec-review
description: Review engineering requirements, specifications, and plans against governing requirements and approved decisions, using ce-doc-review. Require independent subagent re-review after correcting document review findings.
---

# Specification and plan review

Use the installed `ce-doc-review` skill where applicable and read its `SKILL.md` in full. Apply to requirements, specifications, and plans. In OpenSpec projects, first read `openspec/README.md`, relevant specifications, and current change documents, and use available OpenSpec skills. Keep plans and verification evidence inside the existing change structure; avoid duplicate specifications and plans.

## Establish governing sources

Give reviewers readable paths to the documents being reviewed, applicable main specifications, general requirements, project guidance, and evidence of approved decisions. Require them to read these sources, not just a summary of the proposed changes. Distinguish proposals from agreed requirements and acceptance scenarios.

Check specific scenarios and exceptions against the general requirements. Report contradictions with references to both conflicting statements. Greater specificity or detail does not itself establish an agreed exception: require explicit evidence of approval. If a governing source or approval evidence cannot be found, report the gap and its effect rather than inventing an exception.

## Evaluate findings and correct documents

The main agent evaluates findings against the governing sources and fixes substantiated issues within authorized scope. Record the rationale for accepting or rejecting disputed findings; reopen rejected findings only when new evidence warrants it. Keep decisions and verification evidence in the project's established artifact structure, including the existing OpenSpec change when applicable.

## Independent re-review after corrections

After fixing document review findings, including findings in requirements, specifications, and plans, have a separate subagent review the updated documents again using `ce-doc-review` where applicable. Provide the updated documents and governing source paths, and require source reading again. Main-agent self-review does not satisfy independent re-review. A reviewer may be reused if it remains separate from the editing main agent and inspects the current documents.

Evaluate the new findings, fix substantiated issues, and repeat corrections and independent review until no substantiated serious findings remain. Minor recommendations do not block completion.

If repeated reviews make no meaningful progress, or resolving a serious finding requires additional authorization or a user decision, report the blocker and unresolved serious findings. Do not repeat unchanged cycles or declare the work complete. If a required skill or separate reviewer is unavailable, report the limitation and remaining review requirement; continue only independent authorized work.

Report the documents and governing sources reviewed, review coverage, actual corrections and checks, unresolved decisions, remaining serious findings or minor recommendations, and material limitations. Review does not authorize commits, pushes, publishing, or other external actions.
