---
domain: groups
references:
- kind: code
  role: implementation
  target: apps/api/src/services/groups.ts#setGroupGrant
- kind: code
  role: implementation
  target: apps/api/src/services/access.ts#effectiveProjectRole
---

# Project grant

The role one group holds on one project. Inside that project the strongest grant across a member's groups replaces their workspace role.

## Information kept

- **Role** — Viewer, Member or Admin inside the project
