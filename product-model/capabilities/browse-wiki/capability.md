---
availability:
- place: web::workspace
- place: mcp
domain: wiki
references:
- kind: code
  role: implementation
  target: apps/api/src/services/wiki.ts#getWikiTree
- kind: code
  role: implementation
  target: apps/api/src/services/wiki.ts#searchWiki
- kind: code
  role: implementation
  target: apps/api/src/services/wiki.ts#listWikiPages
---

# Browse wiki

A member browses the wiki as a page tree or a filtered list, or searches it in full text. Workspace pages are visible to every member; project pages only to those who can see the project.
