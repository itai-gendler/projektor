---
domain: sprints
relations:
- entity: issue
  verb: includes
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: apps/api/src/services/sprints.ts#createSprint
- kind: code
  role: implementation
  target: apps/web/src/islands/SprintManager.tsx
---

# Sprint

A time box in a project that issues are planned into.

## Information kept

- **Name** — the sprint's name
- **Goal** — what the sprint aims to achieve
- **Start date** — when it starts
- **End date** — when it ends

## States

### Planned

Created and not started.

### Active

Running.

### Completed

Finished; its issues stay planned into it.
