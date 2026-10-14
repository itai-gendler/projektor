---
type: agent
actors:
- ai-agent
entryPoints:
- agent: /mcp/<workspace-id>
references:
- kind: code
  role: implementation
  target: apps/api/src/routes/mcp.ts
  title: MCP dispatch
- kind: doc
  role: intent
  target: apps/docs/src/content/docs/agents/tool-catalog.md
  title: MCP tool catalog
- kind: doc
  role: context
  target: apps/docs/src/content/docs/agents/mcp-connection.md
  title: Connecting an agent
---

# MCP server

The workspace's MCP endpoint, the agent's way into Projektor. One connection is bound to one workspace. An agent signs in either through a connector sign-in its person allowed or with an API token, and acts with that person's workspace role and group grants; a read-only credential can only read.
