---
description: Decide whether to handle a task on the current thread or hand it off to a cold, fresh conversation
argument-hint: <task to perform>
---

The user wants this task handled: **$ARGUMENTS**

Before doing anything else, decide where this task should run, then say which you chose and why in one or two sentences.

## Context size assumption

Assume this conversation's context is at approximately **75% capacity** â€” large, but not an emergency. Token cost is real. The default is **go cold** unless there is a strong reason to stay on this thread.

## Decide: continue here, or start cold?

**Continue on the current thread** only when the task genuinely cannot work without this thread's specific context â€” it depends on decisions, code edits, or discoveries made in this exact conversation that cannot reasonably be summarised into a cold-start prompt.

**Start cold (fresh conversation)** in all other cases, including: the task is unrelated to this thread; the task is self-contained; this conversation has covered more than one distinct topic (a reliable signal that accumulated context is broad and noisy); or a well-briefed cold agent would produce an equally good result.

When it's genuinely ambiguous, **prefer cold** â€” the token savings outweigh the cost of writing a slightly fuller prompt.

## Then act

- **If continuing here:** state that briefly, then just do the task in this conversation.
- **If starting cold:** spawn a fresh agent with the Agent tool (`subagent_type: "general-purpose"` â€” do NOT use `"fork"`, which would inherit this conversation's context and defeat the purpose). Pass the task as a self-contained prompt that includes everything the cold agent needs, since it starts with no knowledge of this thread. Relay back what matters from its result.
