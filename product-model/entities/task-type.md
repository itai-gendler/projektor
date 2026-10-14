---
domain: task-types
references:
- kind: code
  role: implementation
  target: apps/api/src/services/task-types.ts#createTaskType
- kind: code
  role: implementation
  target: apps/api/src/services/task-types.ts#seedDefaultTaskTypes
---

# Task type

One type in the workspace's list of issue types. A new workspace has Epic, Story, Task and Bug, with Task the default; the Epic type is what makes an issue an epic.

## Information kept

- **Key** — the stable machine name, unique in the workspace
- **Name** — the label people see
- **Color** — the badge color
- **Icon** — the badge icon
- **Position** — its place in the order
- **Default** — whether new issues get it when no type is given
