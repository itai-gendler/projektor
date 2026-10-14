---
kind: validation
routes:
  web: Web app
steps:
- text: The User uploads a file to a wiki page
  kind: actor
  actor: user
  entities:
  - {entity: wiki-page, effect: reads, facts: [Title]}
  contexts:
    web:
      place: web::workspace::wiki-page
- text: The file would take the workspace past its storage quota
  kind: condition
  actor: user
  entities:
  - {entity: deployment-settings, effect: reads, facts: [Storage quota]}
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::wiki-page
- text: The Product refuses the upload, naming the quota
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace::wiki-page
---

# An upload over the storage quota is refused

## Trigger

A workspace has used up its attachment storage.

## Outcome

Nothing is stored.

## Edge cases

- A file over 50 MB, or of a type that is not allowed, is refused the same way.
