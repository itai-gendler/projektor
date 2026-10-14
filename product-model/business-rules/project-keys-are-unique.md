---
appliesTo:
- type: entity
  id: project
  facts: [Key]
references:
- kind: code
  role: implementation
  target: apps/api/src/services/projects.ts#createProject
---

# A project's key is unique in its workspace

No two projects of one workspace share a key, so every issue ref names one issue.
