# Engineering workflow

Use OpenSpec and Compound Engineering together to turn a product idea or a change request into reviewed requirements, then plan and implement the agreed work.

OpenSpec provides the project's specifications and change workflow. Compound Engineering provides specialist skills for exploring requirements, planning, debugging, implementation, and review. Use the project's approved requirements and keep work in the existing change. After corrections, have an independent reviewer check the changes again.

## How they work together

Choose the endpoint that matches the request.

| Request | Skill and result |
| --- | --- |
| Work through the requirements | `engineering-requirements` returns reviewed requirements, acceptance scenarios, and approval status. |
| Design an OpenSpec change | `engineering-change-planning` takes the proposal through requirements, UI/API/architecture design, and independent review of `tasks.md`. |
| Complete the task end to end | `engineering-workflow` coordinates planning, the two local commits, implementation, verification, and closure. |

The first commit records the reviewed OpenSpec change before implementation. Failed checks or substantiated review findings send the work back for correction and independent re-review as applicable. Once verification passes, the coordinator syncs the specifications, archives the change, and makes the final commit with the implementation, tests, and archived change. [Full OpenSpec cycle](skills/engineering-workflow/SKILL.md#full-openspec-cycle)

In interactive mode, the user resolves material questions and approves the requirements and design. An autonomous full-cycle request delegates those in-scope decisions to the coordinator. Both modes require the same reviews and verification. [Six planning stages](skills/engineering-change-planning/SKILL.md#six-stages)

Use only the stages relevant to the task. In projects without OpenSpec, the set still applies Compound Engineering and the same review rules to the project's existing requirements and plans. It does not initialize OpenSpec automatically.

## Skills

| Skill | Responsibility |
| --- | --- |
| [engineering-setup](skills/engineering-setup/SKILL.md) | Check and prepare OpenSpec or Graphify in the target project when needed; reuse accessible dependencies. |
| [engineering-requirements](skills/engineering-requirements/SKILL.md) | Develop and review requirements for a new product or an existing project change, and record what has been approved. |
| [engineering-change-planning](skills/engineering-change-planning/SKILL.md) | Design an OpenSpec change through a reviewed implementation plan. |
| [engineering-workflow](skills/engineering-workflow/SKILL.md) | Coordinate the full cycle in interactive or autonomous mode. |
| [engineering-code-review](skills/engineering-code-review/SKILL.md) | Require independent code review, evaluate findings, and repeat review after fixes. |
| [engineering-spec-review](skills/engineering-spec-review/SKILL.md) | Review proposals, specifications, designs, and implementation plans against governing sources, with independent re-review after corrections. |

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

After installation, open a new chat and confirm that all six skills and Compound Engineering are available.

```text
Use $engineering-requirements to turn the product brief into first-release requirements.

Use $engineering-change-planning to design OpenSpec change <change-name> through a reviewed tasks.md.

Use $engineering-workflow to complete <task> interactively. Discuss the requirements and design with me.

Use $engineering-workflow to implement <task> autonomously from start to finish.
```

To inspect project readiness separately:

```text
Use $engineering-setup to check readiness for OpenSpec and Graphify in this project.
```

The workflow, requirements, and specification review skills route OpenSpec checks through `engineering-setup`. The example user instructions also route Graphify checks there. A readiness check alone does not initialize unused tools or create graphs.

Skill invocation syntax may differ in other tools. The set does not install itself or run updates automatically.
