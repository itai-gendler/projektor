---
availability:
- place: mcp
domain: wiki
references:
- kind: code
  role: implementation
  target: apps/api/src/services/wiki-watchers.ts#listWikiChanges
---

# Browse wiki changes

An agent polls for the wiki pages created, changed, restored or deleted since a moment, instead of re-reading the wiki.
