---
kind: primary
routes:
  web: Web app
steps:
- text: The User names a new feedback source and optionally lists the origins its widget runs on
  kind: actor
  actor: user
  entities:
  - {entity: feedback-source, effect: reads, facts: []}
  - {entity: feedback, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::feedback
- text: The Product creates the active source and shows its submit token once
  kind: product
  actor: user
  entities:
  - {entity: feedback-source, effect: creates, to: Active, facts: [Name, Description, Allowed origins, Submit token, Created at]}
  contexts:
    web:
      place: web::workspace::feedback
---

# Create a feedback source

## Trigger

The User wants to collect feedback from a product's users.

## Outcome

The source accepts feedback through the token, which is never shown again.
