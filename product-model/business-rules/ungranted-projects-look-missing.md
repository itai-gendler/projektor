---
appliesTo:
- type: entity
  id: project
references:
- kind: code
  role: implementation
  target: apps/api/src/services/access.ts#assertProjectAccess
- kind: doc
  role: intent
  target: apps/docs/src/content/docs/architecture/access-control.mdx
  title: Access control
---

# A project a member was never granted looks as if it does not exist

Asking for a project, or anything in it, that none of one's groups is granted answers not found, never forbidden; a project one can see but not write answers forbidden to a change.

## Rationale

Answering forbidden would confirm the project exists to someone who was never given it.
