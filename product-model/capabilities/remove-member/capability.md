---
availability:
- place: mcp
domain: workspace
references:
- kind: code
  role: implementation
  target: apps/api/src/services/workspaces.ts#removeMember
---

# Remove member

A workspace owner removes another member from the workspace. The removal is remembered, so the deployment settings do not add the person back at their next sign-in.
