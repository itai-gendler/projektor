---
kind: primary
routes:
  web: Web app
steps:
- text: The User opens the project's issues and switches to the board
  kind: actor
  actor: user
  entities:
  - {entity: project, effect: reads, facts: [Name]}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::issues
- text: The Product lists the project's issues in columns by status category, with each issue's priority, assignee and story points
  kind: product
  actor: user
  entities:
  - {entity: issue, effect: reads, facts: [Ref, Title, Type, Priority, Assignee, Story points]}
  - {entity: task-status, effect: reads, facts: [Name, Category]}
  - {entity: project, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::issues
---

# Browse a project's issues on the board

## Trigger

The User wants to see where the project's work stands.

## Outcome

The User sees every issue in the project, grouped by where it is in the workflow.
