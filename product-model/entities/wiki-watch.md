---
domain: wiki
references:
- kind: code
  role: implementation
  target: apps/api/src/services/wiki-watchers.ts#watchWikiPage
---

# Page watch

A person's request to hear about changes to a wiki page, and optionally to every page beneath it.

## Information kept

- **Include subtree** — whether changes to pages beneath it count too
