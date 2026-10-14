---
availability:
- place: web::workspace
domain: connect-agent
references:
- kind: code
  role: implementation
  target: apps/api/src/services/workspaces.ts#revokeToken
---

# Revoke API token

A workspace owner or admin, in their own browser session, revokes a workspace API token.
