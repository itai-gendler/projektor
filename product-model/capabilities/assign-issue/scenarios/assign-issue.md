---
kind: primary
routes:
  web: Web app
steps:
- text: The User picks a member as the assignee
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace::issue
- text: The Product sets the issue's assignee
  kind: product
  actor: user
  entities:
  - {entity: issue, effect: changes, facts: [Assignee]}
  contexts:
    web:
      place: web::workspace::issue
---

# Assign an issue

## Trigger

Someone should own an issue.

## Outcome

The issue shows its assignee and appears in their My Issues.

## Edge cases

- Someone who is not a member of the workspace is refused.
