---
name: engineering-requirements
description: Develop and review requirements for a new product or a change to an existing one. Use when the user wants testable behavior and acceptance scenarios with an explicit approval status before technical planning.
---

# Engineering requirements

Start with the user's idea, brief, or change request. Finish with reviewed requirements and their approval status. Technical design, implementation tasks, and code belong to later work.

## Choose the Git branch before writing

When the request will write requirements or a specification in a Git repository, check the target checkout before the first write. This includes creating an OpenSpec change and handing off to a skill that will save a draft. Reuse the current branch if it is already for the task or the user chose it for this work. Skip the branch check for chat-only work and directories outside Git.

Otherwise, offer to create a task branch (or reuse the matching branch if it exists) or proceed in the current checkout. Honor an explicit choice already made. Follow the project's branch naming rules and any name the user specified. If no name was given, use the task or issue ID with its original spelling and case as the branch name by default. If the ID is missing or ambiguous, ask for it or an explicit branch name before creating a branch. Create or switch branches only with the user's authorization, then verify the selected branch before writing.

## Choose the working document

Read the project instructions and locate the governing requirements, decision records, and any current change for this work. Choose where to keep the draft before asking a skill to write it.

- **OpenSpec project.** Use `engineering-setup` to check readiness. Read the project guidance (including `openspec/README.md` when present), the applicable main specs and active changes. Reuse the matching change or create one for the requested work. Follow the project's schema and installed OpenSpec skills to write just the requirements artifacts. For example, with the standard schema, use a scoped capture in `openspec-explore` where supported to write the proposal and capability spec deltas. Keep proposals in the change until the project's separate adoption step. If a full proposal command also generates design and tasks, use the supported individual artifact instructions instead.
- **Project with its own requirements format.** Create or update the draft in that format and link to its governing sources.
- **No established format.** In a Git project, request a requirements document from `ce-brainstorm` so reviewers have a file to read. In a new directory without a Git root, use the brief and the user's decisions to write a standalone `REQUIREMENTS.md` in the target directory. Adopt OpenSpec only on explicit request.

Read the installed `ce-brainstorm` instructions. If `ce-brainstorm` will write the draft, follow its requirements workflow through capture. If the project has its own format, use the brainstorm questions to clarify who needs the change, its scope, the alternatives, and how to judge success. Hold one discussion and write the decisions directly in the chosen document. Reuse an earlier brainstorm as source material when one already exists.

## Work from the evidence for each capability

For **new behavior**, identify who needs it, what outcome matters, and what falls inside the first release. For **changed behavior**, locate the applicable rules and scenarios. Describe the intended difference and retain relevant guarantees, including exceptions and compatibility constraints. A single change may contain both kinds of work.

When specifications are missing or disagree with implementation, identify what code, tests or reports actually demonstrate. Treat observations as evidence of current behavior. Trace a binding rule or an exception to a governing source or an explicit decision. Ask about unresolved choices that affect behavior and keep the affected requirement open if the answer is unavailable.

Write requirements in terms of observable outcomes. Use concrete acceptance scenarios for the normal case and for consequential boundaries or failures. Record the reasons for material decisions, sources, and questions that could change the scope. In OpenSpec, preserve applicable scenarios when replacing a requirement and run the project's validation for the change.

## Review and hand off

Run `engineering-spec-review` on the resulting documents. Supply readable paths to the brief or decisions, governing rules, and the draft. For the first specification, use the available product sources and identify any missing authority. Follow that skill's correction and independent re-review rules. Schema validation alone does not establish review completion.

Record the handoff with the requirements in the project’s existing structure. Give the document paths, review outcome, approval status and its basis, and any open decision with its effect on planning. Distinguish approval of a particular behavior from approval of the whole draft. Without evidence of approval, record it as pending. If a serious finding, missing review, or unresolved product decision blocks planning, identify the affected scope and report the blocker.

Return this handoff to the user or calling `engineering-workflow`. A requirements-only request ends here. For separately requested planning, pass the canonical paths and decision status to the planner.
