---
kind: primary
routes:
  web: Web app
steps:
- text: The User removes a project from a group
  kind: actor
  actor: user
  entities:
  - {entity: project, effect: reads, facts: [Name]}
  - {entity: group, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::groups
- text: The Product deletes the project grant; members with no other grant on the project no longer find it
  kind: product
  actor: user
  entities:
  - {entity: project-grant, effect: removes}
  - {entity: project, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::groups
---

# Remove a group's project grant

## Trigger

A group's members should no longer reach a project.

## Outcome

The project is hidden from members who had it only through this group.
