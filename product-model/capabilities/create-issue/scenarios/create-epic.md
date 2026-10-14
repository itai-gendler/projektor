---
kind: alternative
routes:
  web: Web app
steps:
- text: The User gives a new epic a title and a priority
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace::epics
- text: The Product creates the issue with the Epic type
  kind: product
  actor: user
  entities:
  - {entity: task-type, effect: reads, facts: [Key]}
  - {entity: issue, effect: creates, to: Backlog, facts: [Ref, Title, Type, Priority, Author kind]}
  contexts:
    web:
      place: web::workspace::epics
---

# Create an epic

## Trigger

A large piece of work begins.

## Outcome

The epic is listed, ready for children.
