---
kind: primary
routes:
  web: Web app
steps:
- text: The User lists a source's new feedback
  kind: actor
  actor: user
  entities:
  - {entity: feedback, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::feedback-source
- text: The Product returns the feedback newest first with its rating, comment, submitter and context
  kind: product
  actor: user
  entities:
  - {entity: feedback, effect: reads, facts: [Rating, Body, Submitter label, Source URL, App version, Received at, Linked issue]}
  - {entity: comment, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::feedback-source
---

# Read new feedback

## Trigger

The User triages what users said.

## Outcome

The User sees the feedback still to be handled.
