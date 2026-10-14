---
entities:
- entity: feedback-source
  shows: [Name, Description, Allowed origins, Created at, Revoked at]
- entity: feedback
  shows: [Rating, Body, Submitter label, Source URL, App version, Received at, Linked issue]
entryPoints:
- web: /feedback/view
references:
- kind: code
  role: implementation
  target: apps/web/src/islands/FeedbackSourceDetail.tsx
- kind: code
  role: implementation
  target: apps/web/src/islands/FeedbackList.tsx
- kind: code
  role: implementation
  target: apps/web/src/islands/FeedbackSourceSettings.tsx
---

# Feedback source

One feedback source: the feedback it received, with triage and conversion controls, and its settings.
