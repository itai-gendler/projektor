---
availability:
- place: web::workspace
- place: mcp
domain: sprints
references:
- kind: code
  role: implementation
  target: apps/api/src/services/sprints.ts#listSprints
- kind: code
  role: implementation
  target: apps/web/src/islands/SprintManager.tsx
---

# Browse sprints

A member lists a project's sprints with their dates, goals and story points.
