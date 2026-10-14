---
appliesTo:
- type: entity
  id: issue
- type: entity
  id: task-status
references:
- kind: code
  role: implementation
  target: apps/api/src/services/task-statuses.ts#updateTaskStatus
---

# An issue's state follows its task status's category

An issue is in the backlog, to do, in progress, in review, done or cancelled according to its task status's category and backlog and review-step flags; changing a status's category moves every issue in it.
