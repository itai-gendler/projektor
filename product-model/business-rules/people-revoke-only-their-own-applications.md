---
appliesTo:
- type: entity
  id: connected-application
  effect: removes
permits:
- related: [{verb: authorizes, entity: user}]
references:
- kind: code
  role: implementation
  target: apps/api/src/services/oauth.ts#revokeConnectorGrant
---

# Only the person who connected an application revokes it

Each person sees and revokes only their own connected applications; no admin can see or revoke someone else's, and an application cannot revoke itself or its siblings.
