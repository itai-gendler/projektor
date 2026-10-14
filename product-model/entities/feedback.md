---
domain: feedback
references:
- kind: code
  role: implementation
  target: apps/api/src/services/feedback.ts#submitFeedback
- kind: code
  role: implementation
  target: apps/api/src/services/feedback.ts#updateFeedbackStatus
---

# Feedback

One piece of end-user feedback received through a feedback source.

## Information kept

- **Rating** — a thumbs up or down, or one to five stars
- **Body** — the free-text comment
- **Submitter label** — who sent it, as the widget describes them
- **Source URL** — the page or content it is about
- **App version** — the version of the product it came from
- **Received at** — when it arrived
- **Linked issue** — the issue it was converted into

## States

### New

Not yet looked at.

### Reviewed

Read and triaged.

### Actioned

Acted on, usually by converting it into an issue.
