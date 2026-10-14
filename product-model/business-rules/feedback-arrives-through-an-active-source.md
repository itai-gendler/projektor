---
appliesTo:
- type: entity
  id: feedback
  effect: creates
permits:
- related: [{verb: submits, entity: feedback-submitter}]
references:
- kind: code
  role: implementation
  target: apps/api/src/services/feedback.ts#submitFeedback
---

# Feedback is accepted only through an active source's current token

A submission is kept only when its token is the current token of a feedback source that is neither paused nor revoked; anyone holding that token may submit.

## Rationale

The token is public by design, like a publishable key, so pausing, rotating and revoking are the controls.
