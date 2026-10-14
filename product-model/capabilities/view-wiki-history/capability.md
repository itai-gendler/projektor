---
availability:
- place: web::workspace
- place: mcp
domain: wiki
references:
- kind: code
  role: implementation
  target: apps/api/src/services/wiki.ts#listWikiRevisions
- kind: code
  role: implementation
  target: apps/api/src/services/wiki.ts#getWikiRevisionDiff
---

# View wiki history

A member lists a page's revisions, opens one, and compares it with another revision or the current content.
