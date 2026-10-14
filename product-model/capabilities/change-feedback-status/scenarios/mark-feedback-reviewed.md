---
kind: primary
routes:
  web: Web app
steps:
- text: The User selects feedback items and marks them reviewed
  kind: actor
  actor: user
  entities:
  - {entity: feedback, effect: reads, facts: [Body, Received at]}
  contexts:
    web:
      place: web::workspace::feedback-source
- text: The Product marks each selected item reviewed
  kind: product
  actor: user
  entities:
  - {entity: feedback, effect: changes, from: New, to: Reviewed, facts: []}
  contexts:
    web:
      place: web::workspace::feedback-source
---

# Mark feedback reviewed

## Trigger

The User has read a batch of feedback.

## Outcome

The items are out of the new queue.
