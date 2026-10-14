---
availability:
- place: web::workspace
- place: mcp
domain: feedback
references:
- kind: code
  role: implementation
  target: apps/api/src/services/feedback-sources.ts#rotateFeedbackSourceToken
---

# Rotate feedback source token

A workspace owner or admin replaces a feedback source's submit token; the old one stops working at once and the source keeps its identity and history.
