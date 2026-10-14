---
appliesTo:
- type: entity
  id: connected-application
  effect: creates
permits:
- related: [{verb: authorizes, entity: user}]
  when:
  - {entity: user, fact: Public viewer, is: 'No'}
references:
- kind: code
  role: implementation
  target: apps/api/src/routes/oauth.ts
- kind: code
  role: implementation
  target: apps/api/src/middleware/auth.ts#isPublicViewer
---

# A person connects an application only for themselves

Allowing an application access is done by the signed-in person it will act for, in their own browser session; an agent's credential and the anonymous public viewer cannot allow access.
