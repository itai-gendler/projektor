---
domain: connect-agent
references:
- kind: code
  role: implementation
  target: apps/api/src/services/workspaces.ts#createToken
- kind: code
  role: implementation
  target: apps/web/src/islands/TokenManager.tsx
---

# API token

A shared workspace token an admin mints for agents and scripts that cannot use the connector sign-in. An agent using it acts as the admin who minted it. The token itself is shown once, when it is created.

## Information kept

- **Name** — what the token is for
- **Scope** — Read only, or Read and write
- **Created at** — when it was minted
- **Expires at** — when it stops working; a token may never expire
- **Last used at** — roughly when it last authenticated a request
