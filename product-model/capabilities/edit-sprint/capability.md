---
availability:
- place: web::workspace
- place: mcp
domain: sprints
references:
- kind: code
  role: implementation
  target: apps/api/src/services/sprints.ts#updateSprint
- kind: code
  role: implementation
  target: apps/web/src/islands/issue-list/SprintBannerSection.tsx
---

# Edit sprint

A member with write access changes a sprint's name, goal, dates or status, which is how a sprint is started.
