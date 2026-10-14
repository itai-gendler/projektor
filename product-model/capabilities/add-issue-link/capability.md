---
availability:
- place: web::workspace
- place: mcp
domain: issues
references:
- kind: code
  role: implementation
  target: apps/api/src/services/issue-links.ts#createLink
---

# Add issue link

A member who can write to both issues' projects links two issues as blocking, blocked by, relating to, duplicating or following from each other.
