---
availability:
- place: mcp
domain: task-statuses
references:
- kind: code
  role: implementation
  target: apps/api/src/services/task-statuses.ts#updateTaskStatus
---

# Edit task status

A workspace owner or admin changes a status's name, category, color, position or flags. Changing its category moves every issue in it to the matching state.
