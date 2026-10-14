---
availability:
- place: mcp
domain: coordination
references:
- kind: code
  role: implementation
  target: apps/api/src/services/agents.ts#heartbeatAgent
- kind: doc
  role: intent
  target: apps/docs/src/content/docs/philosophy/coordination-model.md
  title: Coordination model
---

# Send agent heartbeat

An agent tells Projektor its session is still alive. Every call that names a live session, such as claiming an issue or files, updating an issue or posting a message, does the same.
