---
kind: primary
routes:
  web: Web app
steps:
- text: The User lists the members
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace::groups
- text: The Product returns each member's name, email and workspace role
  kind: product
  actor: user
  entities:
  - {entity: user, effect: reads, facts: [Email, Name]}
  - {entity: workspace-membership, effect: reads, facts: [Role]}
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::groups
---

# List the workspace's members

## Trigger

The User wants to know who is in the workspace.

## Outcome

The User sees every member and their role.
