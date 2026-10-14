---
kind: primary
routes:
  web: Web app
steps:
- text: The User chooses Undo right after deleting a page
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace
- text: The Product brings the page back from the trash
  kind: product
  actor: user
  entities:
  - {entity: wiki-page, effect: changes, from: Trashed, to: Live, facts: [Trashed at]}
  contexts:
    web:
      place: web::workspace
---

# Undo a page deletion

## Trigger

The User deleted the wrong page.

## Outcome

The page is live again where it was.
