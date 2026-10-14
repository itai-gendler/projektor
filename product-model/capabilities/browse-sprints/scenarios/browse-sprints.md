---
kind: primary
routes:
  web: Web app
steps:
- text: The User opens the sprints
  kind: actor
  actor: user
  entities:
  - {entity: sprint, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::sprints
- text: The Product lists the sprints in creation order with their status, dates and goals
  kind: product
  actor: user
  entities:
  - {entity: sprint, effect: reads, facts: [Name, Goal, Start date, End date]}
  contexts:
    web:
      place: web::workspace::sprints
---

# Browse a project's sprints

## Trigger

The User wants to see the project's cadence.

## Outcome

The User sees every sprint of the project.

## Edge cases

- A project the actor cannot see lists no sprints.
