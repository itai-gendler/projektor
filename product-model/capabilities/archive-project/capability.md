---
availability:
- place: web::workspace
- place: mcp
domain: projects
references:
- kind: code
  role: implementation
  target: apps/api/src/services/projects.ts#updateProject
- kind: code
  role: implementation
  target: apps/web/src/islands/ProjectLanding.tsx
---

# Archive project

A workspace owner or admin archives a project, hiding it from the default project list. Share links to its issues stop resolving.
