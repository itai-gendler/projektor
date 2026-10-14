---
appliesTo:
- type: capability
  id: delete-task-status
- type: entity
  id: task-status
  facts: [Default]
references:
- kind: code
  role: implementation
  target: apps/api/src/services/task-statuses.ts#deleteTaskStatus
---

# The default task status and any status in use cannot be deleted

A workspace always has exactly one default status, and a status some issue is in cannot be deleted.
