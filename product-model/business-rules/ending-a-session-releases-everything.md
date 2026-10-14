---
appliesTo:
- type: capability
  id: end-agent-session
- type: capability
  id: finish-work
- type: entity
  id: agent-session
  effect: changes
  to: Ended
references:
- kind: code
  role: implementation
  target: apps/api/src/services/agents.ts#endAgent
---

# Ending a session releases every lease and claim it holds

When a session ends, by end of session, finish of work, or a failed start of work, its held leases and file claims are released as agent ended.
