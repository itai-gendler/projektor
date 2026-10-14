---
availability:
- place: web::workspace
- place: mcp
domain: groups
references:
- kind: code
  role: implementation
  target: apps/api/src/services/groups.ts#deleteGroup
---

# Delete group

A workspace owner or admin deletes a group. Its memberships and project grants go with it, so members lose whatever access only that group gave them on their next request.
