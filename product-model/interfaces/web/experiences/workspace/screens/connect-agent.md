---
entities:
- entity: api-token
  shows: [Name, Scope, Created at, Expires at, Last used at]
  collects: [Name, Scope, Expires at]
- entity: connected-application
  shows: [Application, Access, Connected at, Expires at]
entryPoints:
- web: /settings/tokens
references:
- kind: code
  role: implementation
  target: apps/web/src/islands/TokenManager.tsx
- kind: code
  role: implementation
  target: apps/web/src/islands/ConnectorManager.tsx
- kind: code
  role: implementation
  target: apps/web/src/islands/ConnectAgentGuide.tsx
---

# Connect Agent

How to connect an agent to this workspace, the applications the member has connected, and, for admins, the workspace's API tokens.
