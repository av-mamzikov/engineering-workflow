---
name: engineering-code-review
description: Require independent subagent review using ce-code-review after any implementation that changes code, including small changes. Evaluate findings and repeat review after fixes until no substantiated serious issues remain.
---

# Independent code review

Apply after any implementation that changes code, including small changes. Use the installed `ce-code-review` skill and read its `SKILL.md` in full. Assign the review to a subagent separate from the main agent that made the changes.

## Give the reviewer evidence

Provide the requirements and acceptance scenarios, scope of changes, exact files or diff to review, relevant project guidance, and verification results, including failures and unrun checks. Require the reviewer to inspect the actual updated changes and report findings with file references and concrete consequences.

Stay within the authorized review scope. Committing, pushing, publishing, or changing unrelated files requires separate authorization. If the skill or a separate reviewer is unavailable, report the blocker and remaining review requirement; do not declare the affected implementation complete.

## Resolve and re-review

The main agent evaluates each finding against requirements and evidence. Fix substantiated issues within authorized scope and rerun relevant checks. Record the rationale for accepting or rejecting disputed findings; reopen rejected findings only when new evidence warrants it.

After addressing findings, submit the updated changes to a separate subagent using `ce-code-review` again. A reviewer may be reused, but it must remain separate from the implementing main agent and inspect the current changes. Repeat corrections, relevant verification, and independent review until no substantiated serious findings remain, including behavioral bugs, regressions, requirements violations, and security issues. Minor recommendations do not block completion.

If repeated reviews make no meaningful progress, or resolving a serious issue requires additional authorization or a user decision, report the blocker and unresolved serious findings. Do not repeat unchanged review cycles or declare the task complete.

## Report the outcome

State the review scope, checks actually performed and their results, resolved serious findings, any remaining minor recommendations, and material limitations. Finish only when the required checks are complete and no substantiated serious findings remain.
