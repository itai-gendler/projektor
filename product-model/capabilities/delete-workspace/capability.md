---
availability:
- place: mcp
domain: workspace
references:
- kind: code
  role: implementation
  target: apps/api/src/services/workspaces.ts#deleteWorkspace
---

# Delete workspace

A workspace owner permanently deletes an empty workspace and everything still kept in it. The default workspace cannot be deleted.
