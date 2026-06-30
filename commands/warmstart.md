Decide whether a new conversation is warranted, and if so generate a warm-start prompt and copy it to the clipboard.

## Step 1 — Assess whether to start fresh

Estimate roughly how much of the current context window has been used by the conversation so far. Use this to decide:

- **Stay on thread** if the conversation is still relatively fresh (context usage well under 75%) AND the remaining work is tightly coupled to decisions already made in this conversation that would be hard to reconstruct. Tell the user why, and stop here.
- **Warm-start** (default) if the context is getting full (roughly 75%+), OR if the next task is self-contained enough that a fresh agent could pick it up from a written summary. When in doubt, default to warm-starting.

## Step 2 — Gather context

1. Read `CLAUDE.md` in the current working directory (if it exists).
2. Read the memory index at `C:\Users\PaulOgbeiwi\.claude\projects\{derive the current project slug from the working directory path}\memory\MEMORY.md` if it exists, then read any individual memory files that look relevant to ongoing work.
3. Run `git log --oneline -15` and `git status` to understand the current branch, recent commits, and any uncommitted changes.
4. If there are modified or staged files, read the most relevant ones to understand what is actively being worked on.

## Step 3 — Write the warm-start prompt

Write a self-contained prompt that a fresh Claude Code agent (with zero prior context) could receive and immediately continue the work. Cover:

- The project: what it is, the tech stack, and any non-obvious conventions from CLAUDE.md that affect day-to-day work.
- Current branch and what it is for.
- The immediate task or problem — be specific about what has been done, what is working, and what is not yet resolved.
- Relevant file paths, function names, or error messages the next agent will need.
- Any memory facts that bear on the current task.

Keep it focused — omit anything that can be derived from CLAUDE.md or the codebase itself. The goal is to transfer working state, not document the whole project.

## Step 4 — Copy to clipboard

Copy the prompt to the clipboard using PowerShell:

```powershell
Set-Clipboard -Value @'
{the prompt text}
'@
```

Tell the user the prompt is on their clipboard and ready to paste into a new conversation.