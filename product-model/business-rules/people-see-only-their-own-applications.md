---
appliesTo:
- type: entity
  id: connected-application
  effect: reads
permits:
- related: [{verb: authorizes, entity: user}]
references:
- kind: code
  role: implementation
  target: apps/api/src/services/oauth.ts#listConnectorGrants
---

# A person sees only the applications they connected

The connected applications list is personal.
