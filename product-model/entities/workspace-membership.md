---
domain: workspace
references:
- kind: code
  role: implementation
  target: apps/api/src/services/workspaces.ts#inviteMember
- kind: code
  role: implementation
  target: apps/api/src/services/access.ts#isWorkspaceAdmin
---

# Workspace membership

A person's membership of one workspace and the role they hold there. Owners and admins administer the workspace and see every project in it; members and viewers see only what their groups are granted.

## Information kept

- **Role** — Owner, Admin, Member or Viewer
- **Joined at** — when the person joined the workspace
