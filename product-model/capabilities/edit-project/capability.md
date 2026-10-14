---
availability:
- place: web::workspace
- place: mcp
domain: projects
references:
- kind: code
  role: implementation
  target: apps/api/src/services/projects.ts#updateProject
---

# Edit project

A workspace owner or admin changes a project's name, key, description, agent WIP limit or whether its epics close automatically. The web app edits the description.
