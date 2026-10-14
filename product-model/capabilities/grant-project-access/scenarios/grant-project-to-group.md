---
kind: primary
routes:
  web: Web app
steps:
- text: The User picks a project and a role for a group
  kind: actor
  actor: user
  entities:
  - {entity: project, effect: reads, facts: [Name]}
  - {entity: group, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::groups
- text: The Product gives the group a project grant with that role
  kind: product
  actor: user
  entities:
  - {entity: project-grant, effect: creates, facts: [Role]}
  - {entity: project, effect: reads, facts: []}
  - {entity: group, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::groups
---

# Grant a project to a group

## Trigger

A group's members need to work in a project.

## Outcome

The group's members see the project at the granted role from their next request.
