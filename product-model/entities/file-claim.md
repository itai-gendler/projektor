---
domain: coordination
references:
- kind: code
  role: implementation
  target: apps/api/src/services/file-claims.ts#claimFiles
---

# File claim

A reservation of one repository file path, made for an issue, so two agents working different issues do not edit the same file.

## Information kept

- **Path** — the exact path string claimed
- **Claimed at** — when it was claimed
- **Released at** — when it ended
- **Release reason** — released, expired, agent ended, overridden or issue closed

## States

### Held

In force.

### Released

No longer in force.
