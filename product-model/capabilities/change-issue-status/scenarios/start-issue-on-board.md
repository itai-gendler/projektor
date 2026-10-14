---
kind: primary
routes:
  web: Web app
steps:
- text: The User drags an issue from the To do column into the In progress column
  kind: actor
  actor: user
  entities:
  - {entity: issue, effect: reads, facts: [Ref, Title]}
  contexts:
    web:
      place: web::workspace::issues
- text: The Product moves the issue to the first in-progress status and stamps when work started
  kind: product
  actor: user
  entities:
  - {entity: task-status, effect: reads, facts: [Name, Category]}
  - {entity: issue, effect: changes, from: To do, to: In progress, facts: [Started at]}
  contexts:
    web:
      place: web::workspace::issues
references:
- kind: code
  role: implementation
  target: apps/web/src/islands/issue-list/BoardView.tsx
- kind: code
  role: implementation
  target: apps/web/src/islands/issue-list/useIssueMutations.ts
---

# Drag an issue into progress on the board

## Trigger

The User picks up a piece of work.

## Outcome

The issue is in progress and its cycle time has started.
