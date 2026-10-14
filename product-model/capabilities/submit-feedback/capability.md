---
availability:
- place: feedback-api
domain: feedback
references:
- kind: code
  role: implementation
  target: apps/api/src/services/feedback.ts#submitFeedback
- kind: doc
  role: intent
  target: apps/docs/src/content/docs/guides/feedback-widget-integration.md
  title: Feedback widget integration
---

# Submit feedback

Another product's feedback widget sends one piece of end-user feedback, a rating, a comment or both, with a feedback source's public submit token.
