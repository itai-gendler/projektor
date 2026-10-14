---
availability:
- place: mcp
domain: workspace
references:
- kind: code
  role: implementation
  target: apps/api/src/services/workspaces.ts#createWorkspace
- kind: code
  role: implementation
  target: apps/api/src/mcp/workspaces.ts
---

# Create workspace

Any signed-in person creates a new workspace and becomes its owner. The workspace starts with the default task types, task statuses, custom fields and wiki templates.
