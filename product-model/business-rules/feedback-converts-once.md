---
appliesTo:
- type: capability
  id: convert-feedback-to-issue
- type: entity
  id: feedback
  facts: [Linked issue]
references:
- kind: code
  role: implementation
  target: apps/api/src/services/feedback.ts#convertFeedbackToIssue
---

# Feedback becomes at most one issue

Converting feedback that already has a linked issue is refused.
