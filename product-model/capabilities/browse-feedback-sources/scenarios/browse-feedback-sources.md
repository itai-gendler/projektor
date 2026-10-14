---
kind: primary
routes:
  web: Web app
steps:
- text: The User opens the feedback sources
  kind: actor
  actor: user
  entities:
  - {entity: feedback-source, effect: reads, facts: []}
  - {entity: feedback, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::feedback
- text: The Product lists the sources with their state and a summary of their feedback
  kind: product
  actor: user
  entities:
  - {entity: feedback-source, effect: reads, facts: [Name, Description, Allowed origins, Created at]}
  - {entity: feedback, effect: reads, facts: [Rating, Received at]}
  contexts:
    web:
      place: web::workspace::feedback
---

# Browse a project's feedback sources

## Trigger

The User checks how feedback collection is going.

## Outcome

The User sees each source and what it has received.
