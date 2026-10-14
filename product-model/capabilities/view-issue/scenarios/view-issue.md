---
kind: primary
routes:
  web: Web app
steps:
- text: The User opens an issue by its ref
  kind: actor
  actor: user
  entities:
  - {entity: issue, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::issue
- text: The Product shows the issue's fields, its definition of ready, its children by state and its links
  kind: product
  actor: user
  entities:
  - {entity: issue, effect: reads, facts: [Ref, Title, Body, Type, Priority, Labels, Assignee, Parent, Sprint, Story points, Custom fields, Child rollup, Definition of ready, Needs audit]}
  - {entity: issue-link, effect: reads, facts: [Type]}
  contexts:
    web:
      place: web::workspace::issue
---

# Open an issue

## Trigger

The User needs the full picture of one issue.

## Outcome

The User sees the issue as Projektor keeps it.
