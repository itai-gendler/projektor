---
availability:
- place: web::workspace
- place: mcp
domain: groups
references:
- kind: code
  role: implementation
  target: apps/api/src/services/groups.ts#removeGroupGrant
---

# Remove project grant

A workspace owner or admin takes a project away from a group.
