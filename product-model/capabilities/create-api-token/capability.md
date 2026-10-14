---
availability:
- place: web::workspace
domain: connect-agent
references:
- kind: code
  role: implementation
  target: apps/api/src/services/workspaces.ts#createToken
- kind: code
  role: implementation
  target: apps/api/src/routes/workspaces.ts
---

# Create API token

A workspace owner or admin, in their own browser session, mints a shared workspace API token with a scope and an optional expiry for agents and scripts that cannot use the connector sign-in.
