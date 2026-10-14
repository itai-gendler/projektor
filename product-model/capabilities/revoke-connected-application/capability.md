---
availability:
- place: web::workspace
domain: connect-agent
references:
- kind: code
  role: implementation
  target: apps/api/src/services/oauth.ts#revokeConnectorGrant
- kind: code
  role: implementation
  target: apps/web/src/islands/ConnectorManager.tsx
---

# Revoke connected application

A person withdraws an application they connected. The list holds only the person's own connected applications; nobody can see or revoke anyone else's.
