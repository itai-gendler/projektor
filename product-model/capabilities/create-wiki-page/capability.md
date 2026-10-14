---
availability:
- place: web::workspace
- place: mcp
domain: wiki
references:
- kind: code
  role: implementation
  target: apps/api/src/services/wiki.ts#createWikiPage
---

# Create wiki page

A member creates a wiki page, as a workspace page or in a project, under an optional parent, from scratch or from a template. Workspace pages need a non-viewer workspace role; project pages need write access to the project.
