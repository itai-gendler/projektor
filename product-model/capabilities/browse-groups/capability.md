---
availability:
- place: web::workspace
- place: mcp
domain: groups
references:
- kind: code
  role: implementation
  target: apps/api/src/services/groups.ts#listGroups
- kind: code
  role: implementation
  target: apps/api/src/services/groups.ts#listMemberGroups
---

# Browse groups

A member lists access groups with their members and project grants. Owners and admins see every group and every member's groups, including members with no group, who are marked access pending; other members see only the groups they belong to.
