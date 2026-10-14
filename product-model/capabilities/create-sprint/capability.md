---
availability:
- place: web::workspace
- place: mcp
domain: sprints
references:
- kind: code
  role: implementation
  target: apps/api/src/services/sprints.ts#createSprint
---

# Create sprint

A member with write access to a project creates a sprint in it.
