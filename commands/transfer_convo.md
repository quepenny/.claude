Produce a self-contained handoff brief that lets someone pick up this conversation cold on a different machine. Output it as a single fenced markdown block (so it's easy to copy). Include:

1. **Project** — repo path, tech stack, one-sentence description of what the project is
2. **What we were working on** — the specific task or feature in progress, with enough detail that no prior context is needed
3. **Decisions made** — any non-obvious choices agreed on during this conversation (naming, approach, copy, etc.)
4. **Files changed** — list every file modified or created, with a one-line description of what changed
5. **Current state** — what is done, what is in progress, what is blocked
6. **Next step** — the single most immediate action needed to continue
7. **Pending questions / dependencies** — anything the next session is waiting on (e.g. a file the user needs to provide)

Be specific — include actual file paths, prop names, copy text, and any other concrete detail that would otherwise require re-reading the conversation. Omit anything that can be derived by reading the current codebase.
