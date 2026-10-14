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

# Restore project

A workspace owner or admin brings an archived project back to the default list.
