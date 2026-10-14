---
availability:
- place: web::workspace
- place: mcp
domain: wiki
references:
- kind: code
  role: implementation
  target: apps/api/src/services/wiki.ts#deleteWikiPage
---

# Delete wiki page

A member moves a page to the trash for 30 days. Its children move up to its parent, or go to the trash with it when asked. A workspace page needs a workspace owner or admin; a project page also accepts a member with an Admin grant on the project.
