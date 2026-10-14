---
availability:
- place: web::workspace
- place: mcp
domain: wiki
references:
- kind: code
  role: implementation
  target: apps/api/src/services/wiki.ts#undeleteWikiPage
---

# Restore wiki page

A member with the permission to delete it brings a trashed page back. Pages trashed together come back together.
