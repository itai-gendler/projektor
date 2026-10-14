---
appliesTo:
- type: capability
  id: claim-files
- type: entity
  id: claim-conflict
references:
- kind: code
  role: implementation
  target: apps/api/src/services/file-claims.ts#claimFiles
- kind: code
  role: implementation
  target: packages/db/migrations/0032_claim_conflicts.sql
---

# Every contended file path is recorded as a claim conflict

Each path a claim found held by a live claim is recorded with both issues, whether the claim was refused or forced through. Taking over from a quiet session is not recorded.

## Rationale

A refused claim leaves no other trace, and the record is what the contention heatmap ranks.
