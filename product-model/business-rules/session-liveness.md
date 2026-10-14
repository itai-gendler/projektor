---
appliesTo:
- type: entity
  id: agent-session
  facts: [Last heartbeat]
- type: capability
  id: claim-issue
references:
- kind: code
  role: implementation
  target: apps/api/src/services/agents.ts#heartbeatAgent
- kind: code
  role: implementation
  target: apps/api/src/services/issue-leases.ts#claimIssue
- kind: doc
  role: intent
  target: apps/docs/src/content/docs/philosophy/coordination-model.md
  title: Coordination model
---

# An agent session is live only while it has been heard from in the last 120 seconds

A session that is active and has called within 120 seconds is live; one that goes quiet longer can no longer claim, and what it holds passes to the next claimer. There is no separate expiry job: liveness is read at the moment it matters.
