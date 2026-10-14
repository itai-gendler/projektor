---
availability:
- place: mcp
domain: coordination
references:
- kind: code
  role: implementation
  target: apps/api/src/services/issue-leases.ts#claimIssue
- kind: doc
  role: intent
  target: apps/docs/src/content/docs/philosophy/coordination-model.md
  title: Coordination model
---

# Claim issue

An agent session leases an issue so no other agent picks it up. The lease is refused while another live session holds the issue or while the project already has its agent WIP limit of live leases; a lease held by a session that has gone quiet passes to the claimer.
