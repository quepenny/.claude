---
name: feedback-no-coauthored
description: User does not want Co-Authored-By lines added to git commits
metadata:
  type: feedback
---

Do not add `Co-Authored-By: Claude ...` trailers to git commit messages.

**Why:** User explicitly rejected a commit that included the co-authored line.

**How to apply:** Omit the Co-Authored-By footer from all commits in this repo.