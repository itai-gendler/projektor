---
kind: primary
routes:
  web: Web app
steps:
- text: The User restores the archived project
  kind: actor
  actor: user
  entities:
  - {entity: project, effect: reads, facts: [Name, Archived at]}
  contexts:
    web:
      place: web::workspace::project-overview
- text: The Product clears the project's archived mark
  kind: product
  actor: user
  entities:
  - {entity: project, effect: changes, from: Archived, to: Active, facts: [Archived at]}
  contexts:
    web:
      place: web::workspace::project-overview
---

# Restore an archived project

## Trigger

Work resumes on an archived project.

## Outcome

The project is listed again.
