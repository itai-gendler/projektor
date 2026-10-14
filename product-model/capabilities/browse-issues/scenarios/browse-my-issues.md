---
kind: alternative
routes:
  web: Web app
steps:
- text: The User opens My Issues
  kind: actor
  actor: user
  entities:
  - {entity: issue, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::my-issues
- text: The Product lists the issues assigned to the User in every project they can see
  kind: product
  actor: user
  entities:
  - {entity: issue, effect: reads, facts: [Ref, Title, Priority, Assignee]}
  - {entity: project, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::my-issues
---

# See the issues assigned to me

## Trigger

The User wants their own work list.

## Outcome

The User sees what is theirs across projects.
