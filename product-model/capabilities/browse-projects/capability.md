---
availability:
- place: web::workspace
- place: mcp
domain: projects
references:
- kind: code
  role: implementation
  target: apps/api/src/services/projects.ts#listProjects
- kind: code
  role: implementation
  target: apps/web/src/islands/ProjectList.tsx
---

# Browse projects

A member lists the projects they can see: every project for an owner or admin, otherwise only projects one of their groups is granted. Archived projects are left out unless asked for.
