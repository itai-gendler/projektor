---
appliesTo:
- type: capability
  id: sign-in
- type: capability
  id: remove-member
- type: entity
  id: deployment-settings
references:
- kind: code
  role: implementation
  target: apps/api/src/services/provisioning.ts#ensureUserProvisioned
- kind: code
  role: implementation
  target: apps/api/src/services/workspaces.ts#removeMember
---

# A removed member is not added back by the deployment settings

Once an owner removes someone, signing in again never re-adds them to that workspace, whatever the admin emails, domain map or auto-join role say. Inviting them again clears the removal.

## Rationale

Without it a configuration match would silently undo an explicit removal at the person's next sign-in.
