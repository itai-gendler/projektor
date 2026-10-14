---
kind: primary
routes:
  web: Web app
steps:
- text: The User deletes a group
  kind: actor
  actor: user
  entities:
  - {entity: group, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::groups
- text: The Product deletes the group and its project grants
  kind: product
  actor: user
  entities:
  - {entity: group, effect: removes}
  - {entity: project-grant, effect: removes, with: group}
  - {entity: project, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::groups
---

# Delete a group

## Trigger

A group is no longer needed.

## Outcome

The group is gone and its grants no longer give anyone access.
