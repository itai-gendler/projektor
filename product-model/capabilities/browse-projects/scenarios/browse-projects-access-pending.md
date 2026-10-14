---
kind: edge
routes:
  web: Web app
steps:
- text: The User opens the project list
  kind: actor
  actor: user
  entities:
  - {entity: project, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::projects
- text: The User is a member or viewer and none of their groups holds a project grant
  kind: condition
  actor: user
  entities:
  - {entity: workspace-membership, effect: reads, facts: [Role]}
  - {entity: project-grant, effect: reads, facts: [Role]}
  - {entity: project, effect: reads, facts: []}
  - {entity: group, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::projects
- text: The Product shows access pending instead of an empty list
  kind: product
  actor: user
  entities:
  - {entity: project, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::projects
references:
- kind: code
  role: implementation
  target: apps/web/src/islands/AccessPending.tsx
---

# A member with no grants sees access pending

## Trigger

A newly joined member opens Projektor.

## Outcome

The User learns they are waiting on an admin rather than looking at an empty workspace.
