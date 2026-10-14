---
appliesTo:
- type: entity
  id: project-grant
references:
- kind: code
  role: implementation
  target: apps/api/src/services/access.ts#effectiveProjectRole
- kind: doc
  role: intent
  target: apps/docs/src/content/docs/architecture/access-control.mdx
  title: Access control
---

# Inside a project the strongest group grant replaces a member's workspace role

For a member or viewer, the role inside a project is the strongest role among their groups' grants on it, Viewer below Member below Admin, whatever their workspace role is: a workspace viewer with a Member grant writes there, and a workspace member with only a Viewer grant reads. Owners and admins keep their workspace role in every project. Grant and membership changes apply from the member's next request.

## Rationale

Membership is not access: the workspace role says who someone is, the grants say what they may touch in each project.
