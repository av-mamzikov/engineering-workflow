# Install engineering-workflow

Instructions for Codex or another compatible coding agent installing this set on the user's behalf. Install the user-level skill set and check the Compound Engineering plugin here. OpenSpec and Graphify are checked later in the target project, when used, through `engineering-setup`. Use current official dependency instructions; this document deliberately does not prescribe installation commands.

## Inspect the environment

Read [README.md](README.md), all four files under `skills/*/SKILL.md`, [examples/AGENTS.md](examples/AGENTS.md), and the existing user-level instructions before changing anything. If repository URLs cannot be read, obtain a local checkout and use that path. Cloning alone does not activate skills.

For Codex, use `CODEX_HOME` when set, otherwise `~/.codex`. For other tools, check their current documented skill and instruction locations and compatibility; do not assume Codex paths or invocation syntax apply. Check skill support and independent subagent capability. Report unsupported capabilities and affected work rather than treating an incompatible installation as complete.

Stay within the user's authorized scope and host permissions. Check symlink or redirect targets before writing. Do not commit, push, publish, or modify unrelated settings during installation. Report any required user action.

## Install skills and dependencies

Install these four folders from `skills/` into the user-level skills directory as separate discoverable skills:

- `engineering-setup`
- `engineering-workflow`
- `engineering-code-review`
- `engineering-spec-review`

Inspect existing destination folders first. Leave identical skills unchanged. Back up files before updates, preserve local customizations, and ask if an update requires choosing between conflicting changes. Do not blindly overwrite existing skill folders.

Check whether the Compound Engineering plugin is installed and accessible to the current agent. Reuse a compatible accessible installation, including a user-level one. Verify it provides the `ce-*` capabilities named by the workflow and review skills. These are skills supplied by one plugin, not separate dependencies to install individually.

If the plugin is missing, install it at the user level using its current official instructions and the host's supported plugin mechanism. If an existing plugin lacks a required capability, check compatibility and the supported update path before making an authorized update; do not install duplicate copies or blindly overwrite customizations. Report required activation steps and verify availability after activation when possible.

Do not install or initialize OpenSpec or Graphify, configure projects, or build graphs during this user-level installation. Their plugin capabilities, tooling, and project setup are checked through `engineering-setup` when an operation needs them in a specific project. A project path is not required to install this set.

Report a missing or inaccessible Compound Engineering plugin and the work it blocks. Do not silently treat partial user-level installation as complete or waive mandatory reviews. Deferred OpenSpec and Graphify checks are expected, not user-level installation failures.

## Merge user instructions

Never replace, truncate, or rewrite the user's instruction file from the example. Preserve existing instructions and their wording. Treat `examples/AGENTS.md` as guidance to merge, not a file to copy over the user's file.

Compare all example rules with the existing instructions. Add only missing compatible rules in a clearly delimited `engineering-workflow` block. Reuse an existing block when present; do not append duplicate rules, including rules already expressed elsewhere in the file. Do not remove existing instructions during installation.

If a rule conflicts with an existing instruction or merging would change its meaning, ask the user to resolve it before changing that rule. Greater detail does not automatically establish an approved exception to an existing rule.

Before changing the instruction file, create a uniquely named backup and report its path. If no rules are missing, leave the file unchanged. If the file does not exist, create it with the applicable rules.

## Validate and report

Check that all four installed skills match the intended installation, Compound Engineering is accessible, unrelated instructions remain unchanged, and repeating installation would not add duplicates. Report installed paths, changes, backup paths, plugin status, and limitations. Explicitly report OpenSpec and Graphify as deferred until project use rather than claiming they were verified.

Distinguish file validation from discovery by the host. Ask the user to open a new chat and confirm that all four skills and the Compound Engineering capabilities are available there. Do not claim a live installation or discovery check that was not performed.

## Update

Compare the current repository with installed skills and the instruction block, including the new `engineering-setup` folder when upgrading an older three-skill installation. Check Compound Engineering using current official guidance; leave OpenSpec and Graphify checks for project use. Back up files before changing them and preserve local customizations and unrelated instructions. Resolve conflicting updates explicitly. Do not silently remove older guidance.

## Remove

Remove only skill folders and rules introduced by this set, preserving subsequent edits and other instructions. Use backups as comparison sources. Restore a whole backup only after confirming it will not discard newer instructions. Leave shared dependencies installed unless their removal is separately requested.
