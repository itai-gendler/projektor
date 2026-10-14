---
kind: primary
routes:
  web: Web app
steps:
- text: The User opens the groups list
  kind: actor
  actor: user
  entities:
  - {entity: group, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::groups
- text: The Product lists the groups the actor may see, each with its members and project grants
  kind: product
  actor: user
  entities:
  - {entity: group, effect: reads, facts: [Name, Description, Members]}
  - {entity: project-grant, effect: reads, facts: [Role]}
  - {entity: project, effect: reads, facts: [Name]}
  - {entity: workspace-membership, effect: reads, facts: [Role]}
  contexts:
    web:
      place: web::workspace::groups
---

# Browse groups

## Trigger

The User wants to see who can reach which projects.

## Outcome

The User sees the groups their workspace role lets them see.
