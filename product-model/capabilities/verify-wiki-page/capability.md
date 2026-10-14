---
availability:
- place: web::workspace
- place: mcp
domain: wiki
references:
- kind: code
  role: implementation
  target: apps/api/src/services/wiki.ts#verifyWikiPage
- kind: code
  role: implementation
  target: apps/api/src/services/wiki-freshness.ts
---

# Verify wiki page

A member with write access vouches that a page is still accurate. Pages that declare a verify interval become stale when it elapses and show up in the stale-page queue.
