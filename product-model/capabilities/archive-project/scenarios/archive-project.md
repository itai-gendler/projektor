---
kind: primary
routes:
  web: Web app
steps:
- text: The User archives the project
  kind: actor
  actor: user
  entities:
  - {entity: project, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web::workspace::project-overview
- text: The Product marks the project archived
  kind: product
  actor: user
  entities:
  - {entity: project, effect: changes, from: Active, to: Archived, facts: [Archived at]}
  contexts:
    web:
      place: web::workspace::project-overview
---

# Archive a project

## Trigger

A project's work is over but should be kept.

## Outcome

The project is hidden from the default list and its share links no longer open.
