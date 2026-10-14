---
appliesTo:
- type: capability
  id: delete-workspace
- type: entity
  id: deployment-settings
references:
- kind: code
  role: implementation
  target: apps/api/src/services/workspaces.ts#deleteWorkspace
---

# The default workspace is never deleted, and no workspace is deleted while it has projects

A workspace can be deleted only when it is not the deployment's default workspace and every project in it has been deleted first.

## Rationale

Deleting a workspace removes everything in it at once; requiring its projects to be deleted first makes that loss deliberate.
