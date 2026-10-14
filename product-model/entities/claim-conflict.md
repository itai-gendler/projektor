---
domain: coordination
references:
- kind: code
  role: implementation
  target: apps/api/src/services/file-claims.ts#claimFiles
- kind: code
  role: implementation
  target: packages/db/migrations/0032_claim_conflicts.sql
---

# Claim conflict

A record that a file path was contended: someone tried to claim a path another live claim held, whether the attempt was refused or forced through. It is the only trace a refused claim leaves.

## Information kept

- **Path** — the contended path
- **Losing issue** — the issue the attempt was made for
- **Holding issue** — the issue that held the path
- **Forced** — whether the attempt overrode the holder
- **Occurred at** — when it happened
