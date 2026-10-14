---
appliesTo:
- type: entity
  id: issue
  facts: [Type]
references:
- kind: code
  role: implementation
  target: apps/api/src/services/issues.ts#updateIssue
---

# An epic keeps the Epic type while it has children

Changing an epic to another type is refused until its children are moved or removed.

## Rationale

Otherwise its children would silently drop out of the epic views and rollups.
