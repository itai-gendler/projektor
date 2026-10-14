---
availability:
- place: web::workspace
- place: mcp
domain: wiki
references:
- kind: code
  role: implementation
  target: apps/api/src/services/wiki.ts#getWikiPage
---

# View wiki page

A member opens a wiki page by slug, or by an old slug that still redirects.
