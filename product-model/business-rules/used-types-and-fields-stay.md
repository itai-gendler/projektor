---
appliesTo:
- type: capability
  id: delete-task-type
- type: capability
  id: delete-custom-field
- type: entity
  id: task-type
references:
- kind: code
  role: implementation
  target: apps/api/src/services/task-types.ts#deleteTaskType
- kind: code
  role: implementation
  target: apps/api/src/services/custom-fields.ts#deleteCustomFieldDef
---

# A task type or custom field still in use cannot be deleted

A task type some issue has, or a custom field some issue holds a value for, is refused deletion.
