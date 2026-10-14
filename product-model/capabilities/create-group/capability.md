---
availability:
- place: web::workspace
- place: mcp
domain: groups
references:
- kind: code
  role: implementation
  target: apps/api/src/services/groups.ts#createGroup
---

# Create group

A workspace owner or admin creates an access group with a name unique in the workspace.
