---
availability:
- place: web::workspace
- place: mcp
domain: feedback
references:
- kind: code
  role: implementation
  target: apps/api/src/services/feedback-sources.ts#revokeFeedbackSource
---

# Revoke feedback source

A workspace owner or admin permanently retires a feedback source. Its feedback is kept, but it never accepts another submission.
