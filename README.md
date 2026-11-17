# Engineering workflow

Use OpenSpec and Compound Engineering together to take engineering work from requirements through implementation and independent review.

OpenSpec provides the project's specifications and change workflow. Compound Engineering provides specialist skills for exploring requirements, planning, debugging, implementation, and review. This set connects them: work follows the project's approved requirements, stays in the existing change structure, and returns to independent review after corrections.

## How they work together

1. **Understand the change.** Read project guidance, relevant specifications, and current change documents. Distinguish proposed changes from approved decisions.
2. **Choose the work needed.** Use the relevant Compound Engineering skills and reuse agreed plans. In an OpenSpec change, keep plans and verification evidence alongside that change instead of creating parallel documents.
3. **Check requirements.** Review specifications and plans against the governing requirements. A detailed scenario does not establish an approved exception to a general rule.
4. **Implement and verify.** Work against the approved requirements and acceptance scenarios, using appropriate tests and browser checks.
5. **Review independently.** After any implementation that changes code, including small changes, a separate subagent reviews it. After review fixes, submit the updated code or documents for independent review again. Resolve substantiated serious findings before declaring completion; report blockers when further progress requires a decision or authorization.

Use only the stages relevant to the task. In projects without OpenSpec, the set still applies Compound Engineering and the same review rules to the project's existing requirements and plans. It does not initialize OpenSpec automatically.

## Skills

| Skill | Responsibility |
| --- | --- |
| [engineering-setup](skills/engineering-setup/SKILL.md) | Check and prepare OpenSpec or Graphify in the target project when needed; reuse accessible dependencies. |
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

## Use

After installation, open a new chat and confirm that all four skills and Compound Engineering are available. Project dependencies are checked when needed. For example:

```text
Use $engineering-workflow to work on the existing OpenSpec change <change-name>.
```

To inspect project readiness separately:

```text
Use $engineering-setup to check readiness for OpenSpec and Graphify in this project.
```

The workflow and specification review skills route OpenSpec checks through `engineering-setup`. The example user instructions also route Graphify checks there. A readiness check alone does not initialize unused tools or create graphs.

Skill invocation syntax may differ in other tools. The set does not install itself or run updates automatically.
