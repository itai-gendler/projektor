---
kind: validation
routes:
  web: Web app
steps:
- text: The User changes the type of an epic that still has children
  kind: actor
  actor: user
  entities:
  - {entity: issue, effect: reads, facts: [Type, Child rollup]}
  contexts:
    web:
      place: web::workspace::issue
- text: The Product refuses the change until the children are moved or removed
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace::issue
---

# An epic with children cannot change type

## Trigger

Someone tries to turn an epic into an ordinary issue.

## Outcome

The epic keeps its type and its children stay visible under it.

## Edge cases

- A parent that would make an issue its own ancestor is refused.
