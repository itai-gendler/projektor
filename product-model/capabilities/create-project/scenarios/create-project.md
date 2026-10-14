---
kind: primary
routes:
  web: Web app
steps:
- text: The User gives the new project a name, a key and optionally a description
  kind: actor
  actor: user
  entities:
  - {entity: project, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::projects
- text: The Product creates the project with a slug derived from its name
  kind: product
  actor: user
  entities:
  - {entity: project, effect: creates, to: Active, facts: [Name, Key, Slug, Description, Agent WIP limit]}
  contexts:
    web:
      place: web::workspace::projects
---

# Create a project

## Trigger

The User starts a new body of work.

## Outcome

The project exists; only owners and admins see it until it is granted to a group.

## Edge cases

- A key another project in the workspace already uses is refused as a conflict.
