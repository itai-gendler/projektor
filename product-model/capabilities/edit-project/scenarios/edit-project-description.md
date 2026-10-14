---
kind: primary
routes:
  web: Web app
steps:
- text: The User edits the project's description
  kind: actor
  actor: user
  entities:
  - {entity: project, effect: reads, facts: [Description]}
  contexts:
    web:
      place: web::workspace::project-overview
- text: The Product saves the description
  kind: product
  actor: user
  entities:
  - {entity: project, effect: changes, facts: [Description]}
  contexts:
    web:
      place: web::workspace::project-overview
---

# Edit a project's description

## Trigger

The project's purpose needs explaining.

## Outcome

The overview shows the new description.
