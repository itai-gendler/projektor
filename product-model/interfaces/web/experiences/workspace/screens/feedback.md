---
entities:
- entity: feedback-source
  shows: [Name, Description, Allowed origins, Created at]
  collects: [Name, Description, Allowed origins]
- entity: feedback
  shows: [Rating, Received at]
entryPoints:
- web: /feedback
references:
- kind: code
  role: implementation
  target: apps/web/src/islands/FeedbackSourceGrid.tsx
- kind: code
  role: implementation
  target: apps/web/src/islands/NewSourceModal.tsx
---

# Feedback

A project's feedback sources with a summary of what each collected, and a form to create one.
