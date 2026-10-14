---
availability:
- place: web::workspace
domain: connect-agent
references:
- kind: code
  role: implementation
  target: apps/api/src/services/workspaces.ts#getWorkspaceMcpInfo
- kind: code
  role: implementation
  target: apps/web/src/islands/ConnectAgentGuide.tsx
---

# View agent connection details

A member reads how to connect an agent to this workspace: the MCP address and the command for their agent. Every member can connect their own agent, scoped to their own role and grants.
