---
kind: primary
routes:
  web: Web app
steps:
- text: The User adds one of the members to a group
  kind: actor
  actor: user
  entities:
  - {entity: workspace-membership, effect: reads, facts: [Role]}
  - {entity: group, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::groups
- text: The Product adds the member to the group; the projects it grants appear on the member's next request
  kind: product
  actor: user
  entities:
  - {entity: group, effect: changes, facts: [Members]}
  - {entity: project, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::groups
---

# Add a member to a group

## Trigger

A member needs the access a group carries.

## Outcome

The member sees the group's projects at the group's roles.

## Edge cases

- Someone who is not a member of the workspace cannot be added.
