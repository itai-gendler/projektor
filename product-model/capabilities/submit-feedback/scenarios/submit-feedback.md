---
kind: primary
routes:
  api: Feedback submission API
steps:
- text: The Feedback submitter sends a rating and a comment from the product's widget
  kind: actor
  actor: feedback-submitter
  entities:
  - {entity: comment, effect: reads, facts: []}
  contexts:
    api:
      place: feedback-api
- text: The token is the current token of a source that is neither paused nor revoked
  kind: condition
  entities: []
  contexts:
    api:
      place: feedback-api
- text: The Product keeps the rating and comment as new, for triage
  kind: product
  actor: feedback-submitter
  entities:
  - {entity: feedback, effect: creates, to: New, facts: [Rating, Body, Submitter label, Source URL, App version, Received at]}
  - {entity: comment, effect: reads, facts: []}
  contexts:
    api:
      place: feedback-api
---

# Send feedback from a widget

## Trigger

An end user of another product rates it or comments on it.

## Outcome

The feedback waits in the project for triage.

## Edge cases

- Feedback needs a rating, a comment, or both.
- Allowed origins only decide what a browser is told; the token is what admits the feedback.
