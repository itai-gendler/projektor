---
availability:
- place: web::workspace
- place: mcp
domain: sprints
references:
- kind: code
  role: implementation
  target: apps/api/src/services/sprints.ts#completeSprint
- kind: code
  role: implementation
  target: apps/web/src/islands/SprintManager.tsx
---

# Complete sprint

A member with write access completes an active sprint. Its issues stay in it, done or not.
