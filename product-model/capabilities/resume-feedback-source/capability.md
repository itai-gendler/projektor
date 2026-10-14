---
availability:
- place: web::workspace
- place: mcp
domain: feedback
references:
- kind: code
  role: implementation
  target: apps/api/src/services/feedback-sources.ts#updateFeedbackSource
---

# Resume feedback source

A workspace owner or admin lets a paused feedback source accept feedback again with the same token.
