---
availability:
- place: web::workspace
- place: mcp
domain: groups
references:
- kind: code
  role: implementation
  target: apps/api/src/services/groups.ts#setGroupGrant
---

# Grant project access

A workspace owner or admin gives a group a role on a project, or changes the role a group already has there.
