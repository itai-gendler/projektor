---
kind: primary
routes:
  web: Web app
steps:
- text: The User opens the project list
  kind: actor
  actor: user
  entities:
  - {entity: project, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::projects
- text: The Product lists the active projects the actor can see
  kind: product
  actor: user
  entities:
  - {entity: project, effect: reads, facts: [Name, Key, Description]}
  contexts:
    web:
      place: web::workspace::projects
---

# Browse visible projects

## Trigger

The User wants to pick a project to work in.

## Outcome

The User sees exactly the projects they have access to.
