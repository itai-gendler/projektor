---
entities:
- entity: group
  shows: [Name, Description, Members]
  collects: [Name, Description, Members]
- entity: project-grant
  shows: [Role]
  collects: [Role]
- entity: workspace-membership
  shows: [Role]
- entity: project
  shows: [Name]
- entity: user
  shows: [Email, Name]
entryPoints:
- web: /settings/groups
references:
- kind: code
  role: implementation
  target: apps/web/src/islands/GroupManager.tsx
---

# Groups

The workspace's access groups, their members and project grants, and every member's groups. Members who are not owners or admins see only the groups they belong to.
