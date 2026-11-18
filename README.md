# Engineering workflow

Use OpenSpec and Compound Engineering together to turn a product idea or a change request into reviewed requirements, then plan and implement the agreed work.

OpenSpec provides the project's specifications and change workflow. Compound Engineering provides specialist skills for exploring requirements, planning, debugging, implementation, and review. Use the project's approved requirements and keep work in the existing change. After corrections, have an independent reviewer check the changes again.

## How they work together

1. **Establish the requirements.** Use existing requirements when they cover the work. For a new product or a change to existing behavior, use `engineering-requirements` to develop acceptance scenarios, review them, and record the approval status. A requirements-only request ends with this handoff.
2. **Choose the work needed.** Use the relevant Compound Engineering skills and reuse agreed plans. In an OpenSpec change, keep plans and verification evidence alongside that change instead of creating parallel documents.
3. **Check requirements.** Review specifications and plans against the governing requirements. A detailed scenario does not establish an approved exception to a general rule.
4. **Implement and verify.** Work against the approved requirements and acceptance scenarios, using tests for the affected behavior and relevant browser checks during implementation and after fixes. Before declaring a code change complete, run the full test suite on the final changed state. A component's full suite is sufficient only within an established project verification boundary for that independent component. Report incomplete runs and remaining verification gaps; passing selected tests does not establish that the full suite passed. For documentation-only changes, run the applicable documentation checks.
5. **Review independently.** After any implementation that changes code, including small changes, a separate subagent reviews it. After review fixes, submit the updated code or documents for independent review again. Resolve substantiated serious findings before declaring completion; report blockers when further progress requires a decision or authorization.

Use only the stages relevant to the task. In projects without OpenSpec, the set still applies Compound Engineering and the same review rules to the project's existing requirements and plans. It does not initialize OpenSpec automatically.

## Skills

| Skill | Responsibility |
| --- | --- |
| [engineering-setup](skills/engineering-setup/SKILL.md) | Check and prepare OpenSpec or Graphify in the target project when needed; reuse accessible dependencies. |
| [engineering-requirements](skills/engineering-requirements/SKILL.md) | Develop and review requirements for a new product or an existing project change, and record what has been approved. |
| [engineering-workflow](skills/engineering-workflow/SKILL.md) | Coordinate OpenSpec context, Compound Engineering stages, delegation, and verification. |
| [engineering-code-review](skills/engineering-code-review/SKILL.md) | Require independent code review, evaluate findings, and repeat review after fixes. |
| [engineering-spec-review](skills/engineering-spec-review/SKILL.md) | Check requirements, specifications, and plans against governing sources, with independent re-review after corrections. |

The set adds coordination and review rules to the specialist skills. The main agent remains responsible for evaluating findings, integrating changes, and checking the result. Minor recommendations do not block completion. Commits, pushes, and publishing require the user's authorization.

## Requirements

- The Compound Engineering plugin, which supplies the `ce-*` skills used by the selected stages. Installation of this set checks it and installs it if missing; an accessible user-level installation is reused.
- OpenSpec and Graphify project dependencies, checked through `engineering-setup` before the respective tool is used. They are not installed or initialized by the user-level set installer.
- A coding agent with skill support and independent subagents for mandatory reviews.

Project checks cover the required plugin capabilities, tooling, and configuration for the target project. Only the dependency needed for the requested operation is prepared, using current official instructions. OpenSpec adoption still requires an explicit request. A missing dependency or reviewer is reported together with the work it blocks.

## Install

Give Codex or another compatible coding agent this request:

```text
Install the engineering-workflow skill set. Check the Compound Engineering
plugin and install it if missing, using current official instructions. Follow:
https://github.com/av-mamzikov/engineering-workflow/blob/main/INSTALL.md
```

[INSTALL.md](INSTALL.md) covers installation, updates, and removal. Existing user instructions are preserved: the agent adds only missing compatible rules and asks about conflicts. [examples/AGENTS.md](examples/AGENTS.md) is guidance to merge, not a replacement for your file.

To update an existing installation after this repository changes:

```text
Update my installed skills and instructions using the Update section of
https://github.com/av-mamzikov/engineering-workflow/blob/main/INSTALL.md
Keep my local changes and ask me about conflicts. Tell me what changed
and whether I need to do anything else.
```

## Use

To learn about this project before installing it or choosing a skill:

```text
What is https://github.com/av-mamzikov/engineering-workflow for?
If I start with just an idea, how do I use the skills to define the first
release, plan it, build it, and review it?
Which skill should I use to plan a feature, fix a bug, or review a change?
Show me what I could ask in each case.
```

After installation, open a new chat and confirm that all five skills and Compound Engineering are available. For a new product you can start directly with requirements. For an existing change the workflow routes the request to the same skill.

```text
Use $engineering-requirements to turn the product brief into first-release requirements.

Use $engineering-workflow to prepare and review the requirements for the existing
OpenSpec change <change-name>. Report their approval status.
```

To inspect project readiness separately:

```text
Use $engineering-setup to check readiness for OpenSpec and Graphify in this project.
```

The workflow, requirements, and specification review skills route OpenSpec checks through `engineering-setup`. The example user instructions also route Graphify checks there. A readiness check alone does not initialize unused tools or create graphs.

Skill invocation syntax may differ in other tools. The set does not install itself or run updates automatically.
