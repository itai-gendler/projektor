---
kind: primary
routes:
  web: Web app
steps:
- text: The User enters a title, body, type, priority and optionally an assignee for a new issue
  kind: actor
  actor: user
  entities:
  - {entity: issue, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::issues
- text: The Product creates the issue in the default status with the next ref in the project and records whether its body meets the definition of ready
  kind: product
  actor: user
  entities:
  - {entity: project, effect: reads, facts: [Key]}
  - {entity: issue, effect: creates, to: Backlog, facts: [Ref, Title, Body, Type, Priority, Assignee, Definition of ready, Author kind]}
  contexts:
    web:
      place: web::workspace::issues
---

# File an issue in the backlog

## Trigger

The User has a piece of work to record.

## Outcome

The issue is in the backlog with its own ref.

## Edge cases

- An assignee who is not a member of the workspace is refused.
- Without a type the workspace's default type, Task, is used.
