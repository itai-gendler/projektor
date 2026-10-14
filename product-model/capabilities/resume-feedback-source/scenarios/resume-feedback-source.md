---
kind: primary
routes:
  web: Web app
steps:
- text: The User resumes a paused feedback source
  kind: actor
  actor: user
  entities:
  - {entity: feedback-source, effect: reads, facts: [Name]}
  - {entity: feedback, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::feedback-source
- text: The Product makes the source active again
  kind: product
  actor: user
  entities:
  - {entity: feedback-source, effect: changes, from: Paused, to: Active, facts: []}
  contexts:
    web:
      place: web::workspace::feedback-source
---

# Resume a source

## Trigger

The problem with a paused source is solved.

## Outcome

The source accepts feedback again with its existing token.
