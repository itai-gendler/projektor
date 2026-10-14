---
availability:
- place: web::workspace
- place: mcp
domain: feedback
references:
- kind: code
  role: implementation
  target: apps/api/src/services/feedback.ts#updateFeedbackStatus
- kind: code
  role: implementation
  target: apps/api/src/services/feedback.ts#bulkMarkReviewed
---

# Change feedback status

A member with write access to the project marks feedback new, reviewed or actioned, one item or a selection at a time.
