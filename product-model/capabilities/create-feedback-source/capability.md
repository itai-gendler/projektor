---
availability:
- place: web::workspace
- place: mcp
domain: feedback
references:
- kind: code
  role: implementation
  target: apps/api/src/services/feedback-sources.ts#createFeedbackSource
---

# Create feedback source

A workspace owner or admin creates a feedback source in a project and receives its public submit token once.
