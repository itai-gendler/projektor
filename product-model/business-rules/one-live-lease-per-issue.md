---
appliesTo:
- type: capability
  id: claim-issue
- type: entity
  id: issue-lease
references:
- kind: code
  role: implementation
  target: apps/api/src/services/issue-leases.ts#claimIssue
- kind: doc
  role: intent
  target: apps/docs/src/content/docs/philosophy/coordination-model.md
  title: Coordination model
---

# At most one session holds an issue at a time

An issue has at most one held lease. A claim on an issue a live session holds is refused naming the holder; a lease whose session went quiet is released as expired and passes to the claimer in the same call.
