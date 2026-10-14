---
appliesTo:
- type: context
  context: {place: mcp}
references:
- kind: code
  role: implementation
  target: apps/api/src/auth/scopes.ts#tokenAllows
- kind: code
  role: implementation
  target: apps/api/src/routes/mcp.ts
---

# An agent never does more than the person it acts for

An agent reached through a connected application or an API token acts with the live workspace role and group grants of the person behind it, checked on every call; a credential with only the read scope performs no change at all.

## Rationale

Credentials carry no permissions of their own beyond read or write, so the role and grant check stays the one authority.
