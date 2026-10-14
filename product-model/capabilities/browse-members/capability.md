---
availability:
- place: web::workspace
- place: mcp
domain: workspace
references:
- kind: code
  role: implementation
  target: apps/api/src/services/workspaces.ts#getWorkspaceWithMembers
---

# Browse members

A member lists the workspace's members with their roles; owners and admins also see each member's groups.
