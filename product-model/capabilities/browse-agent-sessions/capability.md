---
availability:
- place: mcp
domain: coordination
references:
- kind: code
  role: implementation
  target: apps/api/src/services/agents.ts#listActiveAgents
---

# Browse agent sessions

An agent lists the live sessions in the workspace, optionally by issue or project, or including sessions that have gone quiet. Ended sessions are never listed.
