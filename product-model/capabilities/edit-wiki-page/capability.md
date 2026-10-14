---
availability:
- place: web::workspace
- place: mcp
domain: wiki
references:
- kind: code
  role: implementation
  target: apps/api/src/services/wiki.ts#updateWikiPage
- kind: code
  role: implementation
  target: apps/api/src/services/wiki.ts#patchWikiPage
---

# Edit wiki page

A member with write access changes a page's title, content or parent, or patches single sections. Each content change keeps the previous content as a revision; a save based on an outdated revision is refused.
