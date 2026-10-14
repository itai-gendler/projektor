---
kind: primary
routes:
  web: Web app
steps:
- text: The User changes a group's name or description
  kind: actor
  actor: user
  entities:
  - {entity: group, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::groups
- text: The Product saves the group
  kind: product
  actor: user
  entities:
  - {entity: group, effect: changes, facts: [Name, Description]}
  contexts:
    web:
      place: web::workspace::groups
---

# Edit a group

## Trigger

A group's purpose changes.

## Outcome

The group carries the new name or description.
