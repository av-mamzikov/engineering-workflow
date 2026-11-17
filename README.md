# Engineering workflow

A set of personal Codex skills extracted from user-level guidance. The instructions remain in English, matching the source.

## Contents

- `skills/engineering-workflow`: relevant Compound Engineering stages, OpenSpec context, delegation, verification, and authorization.
- `skills/engineering-code-review`: independent code review and the fix-and-review loop.
- `skills/engineering-spec-review`: governing requirements, approved exceptions, and independent document re-review after corrections.
- `examples/AGENTS.md`: example guidance to merge into existing user-level instructions. It is not a replacement file or an installation target.

The set uses Compound Engineering, Graphify, and, in OpenSpec projects, the relevant OpenSpec skills. These dependencies are installed separately using their current supported methods; this repository does not vendor or modify them.

## Installation with Codex or another coding agent

Ask Codex or a similar coding agent with filesystem access to install the set and its required dependencies. Copy this request into a new chat:

```text
Install the skills from https://github.com/av-mamzikov/engineering-workflow
and their required dependencies into my coding agent environment.

Before changing anything, read this repository's README.md, all three
SKILL.md files, examples/AGENTS.md, and my existing user-level instructions.
For Codex, use CODEX_HOME when set, otherwise ~/.codex. For another tool,
check its current documented skill and instruction locations and compatibility;
do not assume Codex paths apply. If the tool cannot support a required
capability, including independent subagents, report the limitation.

Install all three folders from skills/ as separate discoverable skills.
Inspect existing destination folders first. Leave identical skills unchanged.
Back up files before updates, preserve local customizations, and ask if an
update requires choosing between conflicting changes. Do not blindly overwrite
existing skill folders.

Install the required Compound Engineering skills and Graphify dependencies,
and the relevant OpenSpec skills for OpenSpec projects. Determine what is
already installed and compatible. Find and follow the current official
installation instructions for missing dependencies; do not rely on remembered
commands or assume one installation method stays valid forever. Verify their
availability afterwards. Report any dependency that cannot be installed and
the work it blocks. Do not silently treat a partial installation as complete.

Never replace, truncate, or rewrite my user-level instruction file from
the example. Treat examples/AGENTS.md as guidance to merge, not a file
to copy over mine. Preserve existing instructions and their wording.
Compare all example rules with existing instructions, and add only missing,
compatible rules in a clearly delimited engineering-workflow block. Reuse
an existing block when present; do not append duplicates. Do not remove
existing rules during installation. If a rule conflicts with an existing
instruction or merging would change its meaning, ask me to resolve it before
changing that rule. A more detailed new rule is not automatically an approved
exception to an existing instruction.

Before changing the instruction file, create a uniquely named backup and
report its path. If no rules are missing, leave the file unchanged. If the
file does not exist, create it with the applicable rules. Check symlink or
redirect targets before writing so the change stays within authorized scope.

Validate installed files, verify dependencies, confirm unrelated instructions
remain unchanged and repeated installation adds no duplicates, and report
installed paths, backups, dependencies, and limitations. Distinguish file
validation from host discovery: ask me to open a new chat to confirm the
three skills and their dependencies are available there.

Do not commit, push, publish, or modify unrelated settings during installation.
Stay within the host's permissions and report any required user action.
```

If the agent cannot access the repository URL, clone it into a directory of your choice and give the agent that local path. Cloning alone does not activate the skills. Resolve reported instruction conflicts before proceeding with the affected changes.

In a new chat, confirm that `engineering-workflow`, `engineering-code-review`, and `engineering-spec-review` are available, along with their dependencies. Then ask to use `$engineering-workflow`. Other tools may use different invocation syntax. Missing dependencies or independent reviewers must be reported; installation does not waive required review.

## Updates and removal

For updates, ask the agent to compare the repository with installed skills and the instruction block, check dependencies using current official guidance, back up files it will change, and preserve local customizations and unrelated instructions. Resolve conflicting updates explicitly. Do not silently remove older guidance.

For removal, ask the agent to remove only skill folders and rules introduced by this set, preserving subsequent edits and other instructions. Use backups as comparison sources. Restore a whole backup only after confirming that it will not discard newer instructions. Leave shared dependencies installed unless their removal is separately requested.

There are no installation scripts or automatic updates. Publishing and installation are separate actions.

## Rule placement

The example preserves the original Graphify, branch naming, UI, and authorization rules, plus short routing to this set. Merge only rules not already present in your instructions.

| Original rules | Destination |
| --- | --- |
| Graphify queries, report fallback, hooks, no manual update after edits | `examples/AGENTS.md`, Graphify section |
| Task ID branch naming, explicit name override, no invented IDs or renaming | `examples/AGENTS.md`, Git branch naming section |
| Inspect existing UI equivalents and reuse conventions | `examples/AGENTS.md`, UI conventions section |
| Default CE usage, stage selection, read full applicable skills | Example routing and `engineering-workflow` |
| Governing requirements, contradictions, approved exceptions | `engineering-spec-review` |
| Independent document re-review after corrections and blocker handling | `engineering-spec-review` |
| Independent review after every code implementation, including small changes | Example routing and `engineering-code-review` |
| Review evidence, fixes, checks, repeat review, disputed findings, serious vs minor | Review skills |
| Delegation scopes, context, main-agent responsibility | `engineering-workflow` |
| OpenSpec sources, skills, approved decisions, existing change artifacts | `engineering-workflow` and specification review guidance |
| Relevant stages, agreed plans, tests, scenarios, actual results and limitations | `engineering-workflow` |
| Autonomous work within scope, no expanded external-action authority | Example guidance and workflow safeguards |
