---
availability:
- place: web::workspace
- place: mcp
domain: wiki
references:
- kind: code
  role: implementation
  target: apps/api/src/services/wiki-drafts.ts#discardWikiDraft
---

# Discard wiki draft

A member throws away their draft of a page, or the draft is cleared when they publish.
