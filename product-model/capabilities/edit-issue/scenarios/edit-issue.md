---
kind: primary
routes:
  web: Web app
steps:
- text: The User changes the issue's title, body, priority or story points
  kind: actor
  actor: user
  entities:
  - {entity: issue, effect: reads, facts: [Title, Body, Priority]}
  contexts:
    web:
      place: web::workspace::issue
- text: The Product saves the issue and re-checks its body against the definition of ready
  kind: product
  actor: user
  entities:
  - {entity: issue, effect: changes, facts: [Title, Body, Priority, Story points, Definition of ready]}
  contexts:
    web:
      place: web::workspace::issue
---

# Edit an issue's details

## Trigger

The User refines what the issue says.

## Outcome

The issue shows the new details and readiness.
