---
kind: primary
routes:
  web: Web app
steps:
- text: The User clears the issue's assignee
  kind: actor
  actor: user
  entities:
  - {entity: issue, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::issue
- text: The Product leaves the issue unassigned
  kind: product
  actor: user
  entities:
  - {entity: issue, effect: changes, facts: [Assignee]}
  contexts:
    web:
      place: web::workspace::issue
---

# Unassign an issue

## Trigger

An issue's owner steps away from it.

## Outcome

The issue has no assignee.
