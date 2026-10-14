---
availability:
- place: web::workspace
- place: mcp
domain: groups
references:
- kind: code
  role: implementation
  target: apps/api/src/services/groups.ts#addGroupMember
---

# Add group member

A workspace owner or admin adds a workspace member to a group.
