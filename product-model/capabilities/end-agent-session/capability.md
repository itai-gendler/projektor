---
availability:
- place: mcp
domain: coordination
references:
- kind: code
  role: implementation
  target: apps/api/src/services/agents.ts#endAgent
- kind: doc
  role: intent
  target: apps/docs/src/content/docs/philosophy/coordination-model.md
  title: Coordination model
---

# End agent session

An agent ends its own session, which releases every issue lease and file claim it still holds.
