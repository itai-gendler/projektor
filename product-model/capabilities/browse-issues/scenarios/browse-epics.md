---
kind: alternative
routes:
  web: Web app
steps:
- text: The User opens the epics
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace::epics
- text: The Product lists the epics with how many of their visible children are in each state
  kind: product
  actor: user
  entities:
  - {entity: issue, effect: reads, facts: [Ref, Title, Priority, Child rollup]}
  contexts:
    web:
      place: web::workspace::epics
---

# Follow epics' progress

## Trigger

The User tracks large pieces of work.

## Outcome

The User sees how far each epic has come.
