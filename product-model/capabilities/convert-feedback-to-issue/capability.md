---
availability:
- place: web::workspace
- place: mcp
domain: feedback
references:
- kind: code
  role: implementation
  target: apps/api/src/services/feedback.ts#convertFeedbackToIssue
- kind: code
  role: implementation
  target: apps/api/src/services/feedback.ts#bulkConvertToIssue
---

# Convert feedback to issue

A member with write access to the project turns feedback into an issue in that project. The issue's title comes from the comment, or from the rating when there is none, and the feedback is linked to it and marked actioned.
