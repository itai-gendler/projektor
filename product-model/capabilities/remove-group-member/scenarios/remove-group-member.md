---
kind: primary
routes:
  web: Web app
steps:
- text: The User removes a member from a group
  kind: actor
  actor: user
  entities:
  - {entity: group, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::groups
- text: The Product takes the member out of the group; access only it gave ends on their next request
  kind: product
  actor: user
  entities:
  - {entity: group, effect: changes, facts: [Members]}
  contexts:
    web:
      place: web::workspace::groups
---

# Remove a member from a group

## Trigger

A member should lose a group's access.

## Outcome

The member no longer sees projects only that group granted.
