---
kind: alternative
routes:
  web: Web app
steps:
- text: The User moves an issue from In review back to In progress
  kind: actor
  actor: user
  entities:
  - {entity: issue, effect: reads, facts: [Ref, Title]}
  contexts:
    web:
      place: web::workspace::issue
- text: The Product moves the issue back and counts a review bounce
  kind: product
  actor: user
  entities:
  - {entity: issue, effect: changes, from: In review, to: In progress, facts: [Review bounces]}
  contexts:
    web:
      place: web::workspace::issue
---

# Send an issue back from review

## Trigger

Review finds more work to do.

## Outcome

The issue is in progress again and the bounce shows in the metrics.
