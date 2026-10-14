---
kind: alternative
routes:
  web: Web app
steps:
- text: The User picks a different role for a project the group already holds
  kind: actor
  actor: user
  entities:
  - {entity: project, effect: reads, facts: [Name]}
  - {entity: group, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::groups
- text: The Product replaces the role on the existing project grant
  kind: product
  actor: user
  entities:
  - {entity: project-grant, effect: changes, facts: [Role]}
  - {entity: project, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::groups
---

# Change the role a group holds on a project

## Trigger

A group's members need more or less access to a project.

## Outcome

The group holds the project at the new role.
