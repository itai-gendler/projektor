---
domain: coordination
references:
- kind: code
  role: implementation
  target: apps/api/src/services/issue-leases.ts#claimIssue
---

# Issue lease

An agent session's exclusive hold on one issue, so no two agents pick up the same ticket.

## Information kept

- **Claimed at** — when the session took it
- **Released at** — when it ended
- **Release reason** — released, expired, agent ended or issue closed

## States

### Held

In force; counts toward the project's agent WIP limit while its session is live.

### Released

No longer in force.
