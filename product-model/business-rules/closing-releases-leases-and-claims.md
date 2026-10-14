---
appliesTo:
- type: capability
  id: change-issue-status
- type: entity
  id: issue-lease
  effect: changes
  to: Released
references:
- kind: code
  role: implementation
  target: apps/api/src/services/issue-leases.ts#buildReleaseLeaseForClosedIssueStatement
- kind: code
  role: implementation
  target: apps/api/src/services/file-claims.ts#buildReleaseClaimsForClosedIssueStatement
---

# Closing an issue releases its lease and file claims

When an issue moves to a done or cancelled status, by anyone, its live lease and its file claims are released as issue closed.

## Rationale

A finished issue must not keep blocking the fleet on work no one is doing.
