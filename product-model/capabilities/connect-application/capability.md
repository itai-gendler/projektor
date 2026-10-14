---
availability:
- place: web::workspace
domain: connect-agent
references:
- kind: code
  role: implementation
  target: apps/api/src/routes/oauth.ts
- kind: code
  role: implementation
  target: apps/api/src/services/oauth.ts#lookupConsentWorkspace
- kind: doc
  role: context
  target: apps/docs/src/content/docs/agents/mcp-connection.md
  title: Connect Claude
---

# Connect application

A signed-in person allows an application, such as their Claude connector, to reach one workspace on their behalf with the access it asked for. The application can never do more than the person can.
