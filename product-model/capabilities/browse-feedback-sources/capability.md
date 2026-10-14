---
availability:
- place: web::workspace
- place: mcp
domain: feedback
references:
- kind: code
  role: implementation
  target: apps/api/src/services/feedback-sources.ts#listFeedbackSources
- kind: code
  role: implementation
  target: apps/api/src/services/feedback.ts#getFeedbackSummary
---

# Browse feedback sources

A workspace owner or admin lists a project's feedback sources with a short preview of each token, never the token itself, and a summary of what each received.
