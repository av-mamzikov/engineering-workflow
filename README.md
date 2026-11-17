# Engineering workflow

A set of personal Codex skills extracted from an existing user-level `AGENTS.md`. The instructions remain in English, matching the source.

## Contents

- `AGENTS.md`: shortened user-level guidance; install together with all three skills.
- `skills/engineering-workflow`: selects relevant Compound Engineering stages, handles OpenSpec context, delegation, verification, and authorization.
- `skills/engineering-code-review`: independent code review and the fix-and-review loop.
- `skills/engineering-spec-review`: governing requirements, approved exceptions, and independent document re-review after corrections.

The set complements existing skills. It does not include or modify Compound Engineering, Graphify, or OpenSpec skills.

## Local installation

Cloning this repository does not activate the skills. Back up the current user-level `AGENTS.md` before replacing it.

1. Install the applicable Compound Engineering skills named in the workflow table. Keep the existing Graphify skill and any project-required OpenSpec skills available.
2. Copy each of the three skill folders from `skills/` into your Codex user skills directory (`$CODEX_HOME/skills`, or `~/.codex/skills/` when unset). Copy the folders themselves, not a single enclosing `engineering-workflow/skills` directory.
3. Replace the user-level `$CODEX_HOME/AGENTS.md` (default `~/.codex/AGENTS.md`) with the supplied `AGENTS.md` after checking any newer local changes.
4. Check that all three skills are visible in a new chat before relying on the shortened guidance.

For the Windows setup used to author this set, run the following in PowerShell from the parent directory where you want to create the clone. The first two commands clone the repository and enter it:

```powershell
git clone https://github.com/av-mamzikov/engineering-workflow.git
Set-Location engineering-workflow

$codexUserDir = if ($env:CODEX_HOME) { $env:CODEX_HOME } else { Join-Path $env:USERPROFILE '.codex' }
$skillTargetDir = Join-Path $codexUserDir 'skills'
$skillNames = @('engineering-workflow', 'engineering-code-review', 'engineering-spec-review')

# Stop rather than overwrite any existing skill folder.
foreach ($skillName in $skillNames) {
    if (Test-Path -LiteralPath (Join-Path $skillTargetDir $skillName)) {
        throw "Skill already exists: $skillName. Back it up and compare before updating."
    }
}
New-Item -ItemType Directory -Path $skillTargetDir -Force -ErrorAction Stop | Out-Null
foreach ($skillName in $skillNames) {
    Copy-Item -LiteralPath (Join-Path 'skills' $skillName) -Destination $skillTargetDir -Recurse -ErrorAction Stop
}

# Review the supplied AGENTS.md before running the replacement below.
$userAgentsPath = Join-Path $codexUserDir 'AGENTS.md'
if (Test-Path -LiteralPath $userAgentsPath) {
    $agentsBackupPath = "$userAgentsPath.backup-$(Get-Date -Format 'yyyyMMdd-HHmmss-fff')"
    Copy-Item -LiteralPath $userAgentsPath -Destination $agentsBackupPath -ErrorAction Stop
    Write-Output "Backup: $agentsBackupPath"
}
Copy-Item -LiteralPath 'AGENTS.md' -Destination $userAgentsPath -ErrorAction Stop
```

On other platforms, follow the same manual copy steps using your shell. For updates, pull repository changes, compare installed files, and back them up before replacement; the first-install example deliberately stops when skill folders already exist. To roll back, restore the saved `AGENTS.md` and remove only the three skill folders installed from this set, or restore their previous backups.

In a new chat, ask to use `$engineering-workflow`, `$engineering-code-review`, or `$engineering-spec-review`. Confirm they appear in the available skills. These commands do not install the third-party dependencies: if a named skill is absent, the workflow reports the missing dependency and affected work.

There are no installation scripts or automatic updates. Publishing the repository and installing it are separate actions.

## Rule placement

| Original rules | Destination |
| --- | --- |
| Graphify query order, focused commands, report fallback, hooks, no manual update after edits | `AGENTS.md`, Graphify section |
| Task ID branch naming, explicit name override, no invented IDs or renaming | `AGENTS.md`, Git branch naming section |
| Inspect existing UI equivalents and reuse project conventions | `AGENTS.md`, UI conventions section |
| Default CE usage, stage selection, read full applicable skills | `AGENTS.md` routing and `engineering-workflow` |
| Main specs and general requirements; contradictions and approved exceptions | `engineering-spec-review` |
| Independent document re-review after corrections; evaluate, repeat, stop on blockers | `engineering-spec-review` |
| Independent review after every code implementation, including small changes | `AGENTS.md` routing and `engineering-code-review` |
| Review evidence, fixes, checks, repeat review, disputed findings, serious vs minor | Review skills |
| Conditional delegation, example scopes, context and main-agent responsibility | `engineering-workflow` |
| OpenSpec sources, available skills, approved decisions, existing change artifacts | `engineering-workflow` and relevant specification review guidance |
| Relevant stages, agreed plans, tests, scenarios, actual results and limitations | `engineering-workflow` |
| Autonomous work within scope; no expanded external-action authority | `AGENTS.md` and workflow safeguards |

Unavailable dependencies or reviewers must be reported rather than silently waiving mandatory review. This clarifies failure handling without replacing the original requirements.
