---
kind: primary
routes:
  web: Web app
steps:
- text: The User names a new group and describes it
  kind: actor
  actor: user
  entities:
  - {entity: group, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::groups
- text: The Product creates the group with no members and no project grants
  kind: product
  actor: user
  entities:
  - {entity: group, effect: creates, facts: [Name, Description, Members]}
  - {entity: project-grant, effect: reads, facts: []}
  - {entity: project, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::groups
---

# Create a group

## Trigger

The User wants to give a set of people access to some projects.

## Outcome

An empty group exists, ready for members and grants.

## Edge cases

- A name another group in the workspace already uses is refused as a conflict.
