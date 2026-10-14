---
availability:
- place: web::workspace
- place: mcp
domain: groups
references:
- kind: code
  role: implementation
  target: apps/api/src/services/groups.ts#removeGroupMember
---

# Remove group member

A workspace owner or admin takes a member out of a group.
