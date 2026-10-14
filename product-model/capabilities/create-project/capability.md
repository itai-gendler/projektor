---
availability:
- place: web::workspace
- place: mcp
domain: projects
references:
- kind: code
  role: implementation
  target: apps/api/src/services/projects.ts#createProject
---

# Create project

A workspace owner or admin creates a project with a name and a key unique in the workspace, optionally a description and an agent WIP limit.
