# Install engineering-workflow

Instructions for Codex or another compatible coding agent installing this set on the user's behalf. Use the current official installation guidance for dependencies; this document deliberately does not prescribe their installation commands.

## Inspect the environment

Read [README.md](README.md), all three files under `skills/*/SKILL.md`, [examples/AGENTS.md](examples/AGENTS.md), and the existing user-level instructions before changing anything. If repository URLs cannot be read, obtain a local checkout and use that path. Cloning alone does not activate skills.

For Codex, use `CODEX_HOME` when set, otherwise `~/.codex`. For other tools, check their current documented skill and instruction locations and compatibility; do not assume Codex paths or invocation syntax apply. Check skill support and independent subagent capability. Report unsupported capabilities and affected work rather than treating an incompatible installation as complete.

Stay within the user's authorized scope and host permissions. Check symlink or redirect targets before writing. Do not commit, push, publish, or modify unrelated settings during installation. Report any required user action.

## Install skills and dependencies

Install these three folders from `skills/` as separate discoverable skills:

- `engineering-workflow`
- `engineering-code-review`
- `engineering-spec-review`

Inspect existing destination folders first. Leave identical skills unchanged. Back up files before updates, preserve local customizations, and ask if an update requires choosing between conflicting changes. Do not blindly overwrite existing skill folders.

Check what is already installed and compatible. Install missing dependencies using their current official instructions:

- The Compound Engineering skills named by this set's workflow and review instructions.
- The Graphify skill and its required tooling for the example codebase guidance.
- The relevant OpenSpec skills and tooling when the target project uses OpenSpec.

Verify dependency availability afterwards. Do not initialize OpenSpec in projects that do not use it as part of installing this set. Report dependencies that cannot be installed and the work they block. Do not silently treat partial installation as complete or waive mandatory reviews.

## Merge user instructions

Never replace, truncate, or rewrite the user's instruction file from the example. Preserve existing instructions and their wording. Treat `examples/AGENTS.md` as guidance to merge, not a file to copy over the user's file.

Compare all example rules with the existing instructions. Add only missing compatible rules in a clearly delimited `engineering-workflow` block. Reuse an existing block when present; do not append duplicate rules, including rules already expressed elsewhere in the file. Do not remove existing instructions during installation.

If a rule conflicts with an existing instruction or merging would change its meaning, ask the user to resolve it before changing that rule. Greater detail does not automatically establish an approved exception to an existing rule.

Before changing the instruction file, create a uniquely named backup and report its path. If no rules are missing, leave the file unchanged. If the file does not exist, create it with the applicable rules.

## Validate and report

Check that all three installed skills match the intended installation, dependencies are available, unrelated instructions remain unchanged, and repeating installation would not add duplicates. Report installed paths, changes, backup paths, dependency status, and limitations.

Distinguish file validation from discovery by the host. Ask the user to open a new chat and confirm that all three skills and their dependencies are available there. Do not claim a live installation or discovery check that was not performed.

## Update

Compare the current repository with installed skills and the instruction block. Check dependencies using current official guidance, back up files before changing them, and preserve local customizations and unrelated instructions. Resolve conflicting updates explicitly. Do not silently remove older guidance.

## Remove

Remove only skill folders and rules introduced by this set, preserving subsequent edits and other instructions. Use backups as comparison sources. Restore a whole backup only after confirming it will not discard newer instructions. Leave shared dependencies installed unless their removal is separately requested.
