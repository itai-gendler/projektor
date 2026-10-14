---
kind: system
acts: external
relations:
- entity: agent-session
  verb: runs
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: apps/api/src/middleware/auth.ts#authMiddleware
- kind: code
  role: implementation
  target: apps/api/src/auth/scopes.ts#tokenAllows
---

# AI agent

A person's AI coding agent connected to a workspace's MCP server. It acts as the person it is connected for: a connector sign-in that person allowed, or an API token that person minted.

## Information kept

- **Credential** — how it signs in: a connector sign-in, a workspace API token or a personal token
- **Scope** — Read only, or Read and write
