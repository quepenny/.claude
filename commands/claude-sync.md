Sync this Claude config repo so settings are consistent across machines.

1. Run `git status` to see modified and untracked files.
2. For each file or directory, decide: is it machine-agnostic config that should travel with the repo, or is it machine-specific / ephemeral?
   - **Commit**: config files, commands, skills, settings that apply on any machine (e.g. `settings.json`, `commands/`, `CLAUDE.md`)
   - **Gitignore**: anything machine-specific (absolute paths, local memory, lock files without a manifest) or ephemeral (caches, session data, update logs)
3. Update `.gitignore` for anything in the ignore category that isn't already covered.
4. Stage and commit tracked changes with a concise message describing what changed.

Do not push — stop after committing and report what was committed vs. ignored.
