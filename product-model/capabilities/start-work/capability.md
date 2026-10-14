---
availability:
- place: mcp
domain: coordination
references:
- kind: code
  role: implementation
  target: apps/api/src/services/agents.ts#startWork
- kind: doc
  role: context
  target: AGENTS.md
  title: Fleet coordination protocol
---

# Start work

In one call an agent registers a session, leases an issue, claims the files it will edit and posts that it started. Any conflict ends the session and leaves nothing claimed.
