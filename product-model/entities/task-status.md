---
domain: task-statuses
references:
- kind: code
  role: implementation
  target: apps/api/src/services/task-statuses.ts#createTaskStatus
- kind: code
  role: implementation
  target: apps/api/src/services/task-statuses.ts#resolveStatus
---

# Task status

One status in the workspace's own list. Its category, and whether it is the backlog or a review step, decide what an issue in it means for readiness, flow timestamps, the completion report gate and closing.

## Information kept

- **Key** — the stable machine name, unique in the workspace
- **Name** — the label people see
- **Category** — To do, In progress, Done or Cancelled
- **Color** — the badge color
- **Position** — its place in the order
- **Default** — whether new issues start in it; exactly one status is the default
- **Review step** — whether entering it hands work in for review
- **Backlog** — whether it is the untriaged backlog
