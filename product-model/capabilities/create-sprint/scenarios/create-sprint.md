---
kind: primary
routes:
  web: Web app
steps:
- text: The User names a sprint and optionally gives it a goal and dates
  kind: actor
  actor: user
  entities:
  - {entity: sprint, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::sprints
- text: The Product creates the sprint as planned
  kind: product
  actor: user
  entities:
  - {entity: sprint, effect: creates, to: Planned, facts: [Name, Goal, Start date, End date]}
  contexts:
    web:
      place: web::workspace::sprints
---

# Plan a sprint

## Trigger

The User plans the next time box.

## Outcome

A planned sprint exists.
