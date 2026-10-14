---
availability:
- place: web::workspace
- place: mcp
domain: wiki
references:
- kind: code
  role: implementation
  target: apps/api/src/services/wiki.ts#listStaleWikiPages
---

# Browse stale wiki pages

A member lists the pages that need re-verification: their verify interval has elapsed, they declare one but were never verified, or their status says stale.
