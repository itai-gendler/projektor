---
availability:
- place: web::workspace
- place: mcp
domain: feedback
references:
- kind: code
  role: implementation
  target: apps/api/src/services/feedback-sources.ts#updateFeedbackSource
- kind: code
  role: implementation
  target: apps/web/src/islands/FeedbackSourceSettings.tsx
---

# Pause feedback source

A workspace owner or admin stops a feedback source accepting feedback at once, keeping its token, identity and history.
