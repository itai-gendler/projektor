---
availability:
- place: mcp
domain: coordination
references:
- kind: code
  role: implementation
  target: apps/api/src/services/agents.ts#registerAgent
- kind: doc
  role: intent
  target: apps/docs/src/content/docs/philosophy/coordination-model.md
  title: Coordination model
---

# Register agent session

An agent registers a session in the workspace, optionally linked to the issue it means to work, and gets back the session id it names in later coordination calls. The session records the credential it registered with.
