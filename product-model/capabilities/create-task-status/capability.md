---
availability:
- place: mcp
domain: task-statuses
references:
- kind: code
  role: implementation
  target: apps/api/src/services/task-statuses.ts#createTaskStatus
---

# Create task status

A workspace owner or admin adds a status to the workspace's list with a category and optionally makes it the default, the backlog or a review step.
