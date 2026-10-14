---
domain: coordination
relations:
- entity: issue-lease
  verb: holds
  cardinality: one-to-many
- entity: file-claim
  verb: holds
  cardinality: one-to-many
- entity: coordination-message
  verb: posts
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: apps/api/src/services/agents.ts#registerAgent
- kind: doc
  role: intent
  target: apps/docs/src/content/docs/philosophy/coordination-model.md
  title: Coordination model
---

# Agent session

One run of an agent in a workspace, registered when it starts and kept alive by its calls. A session is live while it is active and has been heard from within the last 120 seconds; leases and claims follow their session's liveness.

## Information kept

- **Name** — the name the agent gave itself
- **Linked issue** — the issue it registered for, if any
- **Credential** — the credential it registered with, which lets a lone agent omit its session id later
- **Started at** — when it registered
- **Last heartbeat** — when it was last heard from
- **Ended at** — when it ended

## States

### Active

Registered and not ended; live only while heard from in the last 120 seconds.

### Ended

Ended by the agent or by a finished or failed start of work.
