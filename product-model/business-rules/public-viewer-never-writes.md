---
appliesTo:
- type: context
  context: {place: 'web::workspace'}
- type: entity
  id: deployment-settings
references:
- kind: code
  role: implementation
  target: apps/api/src/services/access.ts#effectiveProjectRole
- kind: code
  role: implementation
  target: apps/api/src/middleware/auth.ts#isPublicViewer
---

# The anonymous public viewer never changes anything

While public read-only access is on, anonymous visitors share one viewer identity. It reads the projects granted to the Public viewers group and is held to read access whatever role that grant carries; it can never allow an application access.

## Rationale

The identity stands for everyone on the internet, so a grant picker's default role must never let the internet write.
