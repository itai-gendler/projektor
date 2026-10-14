---
kind: validation
routes:
  api: Feedback submission API
steps:
- text: The Feedback submitter sends a rating with a paused source's token
  kind: actor
  actor: feedback-submitter
  entities: []
  contexts:
    api:
      place: feedback-api
- text: The token belongs to a paused source
  kind: condition
  entities: []
  contexts:
    api:
      place: feedback-api
- text: The Product refuses the submission as forbidden
  kind: product
  entities: []
  contexts:
    api:
      place: feedback-api
---

# A paused source refuses feedback

## Trigger

A widget keeps submitting after its source was paused.

## Outcome

Nothing is kept.

## Edge cases

- A revoked or unknown token is refused as not found.
