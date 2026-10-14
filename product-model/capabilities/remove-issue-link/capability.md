---
availability:
- place: web::workspace
- place: mcp
domain: issues
references:
- kind: code
  role: implementation
  target: apps/api/src/services/issue-links.ts#deleteLink
---

# Remove issue link

A member who can write to both issues' projects removes a link between them.
