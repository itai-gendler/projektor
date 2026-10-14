---
type: api
actors:
- feedback-submitter
entryPoints:
- api: /api/feedback/submit
references:
- kind: code
  role: implementation
  target: apps/api/src/routes/feedback.ts
- kind: code
  role: implementation
  target: apps/api/src/examples/feedback-widget-submit.ts
- kind: doc
  role: intent
  target: apps/docs/src/content/docs/guides/feedback-widget-integration.md
  title: Feedback widget integration
---

# Feedback submission API

The public endpoint another product's feedback widget posts end-user feedback to. It needs no sign-in: a feedback source's public submit token says which project the feedback belongs to.
