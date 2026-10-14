---
kind: primary
routes:
  web: Web app
steps:
- text: The User opens a planned sprint's details from the issues filtered to it and sets its status to active
  kind: actor
  actor: user
  entities:
  - {entity: sprint, effect: reads, facts: [Name, Start date, End date]}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::issues
- text: The Product saves the sprint as active
  kind: product
  actor: user
  entities:
  - {entity: sprint, effect: changes, from: Planned, to: Active, facts: []}
  contexts:
    web:
      place: web::workspace::issues
---

# Start a sprint

## Trigger

A planned sprint begins.

## Outcome

The sprint is active.
