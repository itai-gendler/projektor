---
kind: alternative
routes:
  web: Web app
steps:
- text: The User closes the last open child of an epic
  kind: actor
  actor: user
  entities:
  - {entity: issue, as: child, effect: reads, facts: [Parent]}
  contexts:
    web:
      place: web::workspace::issue
- text: The Product closes the child
  kind: product
  actor: user
  entities:
  - {entity: issue, as: child, effect: changes, from: In progress, to: Done, facts: [Done at]}
  contexts:
    web:
      place: web::workspace::issue
- text: The epic's project closes epics automatically and the User can write to it
  kind: condition
  actor: user
  entities:
  - {entity: project, effect: reads, facts: [Close epics automatically]}
  contexts:
    web:
      place: web::workspace::issue
- text: The Product closes the epic too
  kind: product
  actor: user
  entities:
  - {entity: issue, as: epic, effect: changes, from: In progress, to: Done, facts: [Done at]}
  contexts:
    web:
      place: web::workspace::issue
---

# Closing an epic's last open child closes the epic

## Trigger

The last piece of an epic is finished in a project set to close epics automatically.

## Outcome

Both the child and its epic are done.

## Edge cases

- If the epic itself cannot close, for example because an agent worked it without a report, it is reported ready to close instead.
