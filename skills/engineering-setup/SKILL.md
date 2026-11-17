---
name: engineering-setup
description: Check and prepare dependencies for a specific project before using OpenSpec or Graphify, or when asked to check project readiness. Reuse an accessible Compound Engineering plugin, including user-level installations, and prepare only dependencies needed for the requested work.
---

# Project dependency setup

Check and prepare dependencies in the target project. The user-level installer handles the engineering-workflow skills.

## Establish scope

Resolve the target project from the user's request or current workspace. Read its applicable instructions and inspect existing dependency configuration. If the project is ambiguous, ask before making project changes.

Check OpenSpec when the task needs OpenSpec. Check Graphify when it needs Graphify. Install only what the task requires. For a general readiness check, inspect both and report their status, but inspection alone is not authorization to initialize unused tools.

## Check the right level

| Dependency | What to check |
| --- | --- |
| Compound Engineering | The plugin is accessible to the current agent and provides the needed `ce-*` skills. An accessible user-level installation is sufficient; do not install another copy in the project. |
| OpenSpec | The required plugin capabilities are available and the target project's OpenSpec installation and configuration are ready for the requested operation. A plugin visible elsewhere does not establish this project's readiness. |
| Graphify | The required plugin capabilities and tooling are available and the target project's Graphify setup is ready for the requested operation. Inspect graph availability separately from tool installation. |

Discover capabilities through the current host and inspect actual project state. Do not equate a directory, an executable, or a plugin listing alone with full readiness. Treat the `ce-*` skills as capabilities of the Compound Engineering plugin, not separate packages to install.

## Prepare what is missing

Read the applicable installed dependency skill in full before using it. Find and follow the dependency's current official installation and project setup instructions; do not rely on remembered commands or assume an installation method is permanent. If a dependency is absent, consult its official instructions before trying to load its skill.

Prepare missing OpenSpec or Graphify dependencies for this project only when needed for the authorized task. Reuse compatible existing installations. Preserve project configuration and instructions, back up existing files before changing them, and leave already-correct setup unchanged on repeated runs. Ask for a decision when configurations conflict rather than overwriting local choices.

Do not initialize OpenSpec in a project that does not use it unless the user explicitly requests adopting or initializing it. A missing OpenSpec setup does not prevent work that uses the project's existing requirements without OpenSpec. Do not create a graph merely to check installation; graph creation must be needed for the requested Graphify operation and follow its skill. Respect existing Graphify refresh and hook rules; do not run `graphify update .` after code edits.

If Compound Engineering is missing or inaccessible, use the plugin-level check and installation guidance in this set's `INSTALL.md` when available, or its current official instructions. Installing this set normally handles that dependency already. Repair it only within the authorized scope; do not install individual `ce-*` skills as a substitute for the plugin.

Setup does not authorize unrelated changes, commits, pushes, publishing, or bypassing host permissions. If an action needs additional authorization or user interaction, describe the concrete action and why it is needed. Continue independent authorized work; do not claim blocked dependency work is complete.

## Verify and hand back

Check the required capabilities and project configuration using the dependency's supported checks. Distinguish installation, host discovery, project initialization, and graph availability. If activation needs a new chat or another user action, report it; files on disk alone do not prove discovery.

Report the target project, dependencies checked, reused installations, changes and backups, checks actually performed, and any remaining blockers with the operations they affect. Return to the original task once its required dependency is ready. Do not waive independent review because setup is incomplete.
