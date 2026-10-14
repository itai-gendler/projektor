---
availability:
- place: web::workspace
- place: mcp
domain: feedback
references:
- kind: code
  role: implementation
  target: apps/api/src/services/feedback.ts#listFeedback
---

# Browse feedback

A member who can see a project lists its feedback, by source or by triage state.
