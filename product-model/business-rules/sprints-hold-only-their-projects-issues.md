---
appliesTo:
- type: capability
  id: move-issues-to-sprint
- type: entity
  id: issue
  facts: [Sprint]
references:
- kind: code
  role: implementation
  target: apps/api/src/services/sprints.ts#moveIssuesToSprint
---

# A sprint holds only issues of its own project

Moving issues into a sprint refuses the whole move when any of them belongs to another project.
