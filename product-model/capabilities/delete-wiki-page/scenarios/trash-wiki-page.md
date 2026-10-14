---
kind: primary
routes:
  web: Web app
steps:
- text: The User deletes a page
  kind: actor
  actor: user
  entities:
  - {entity: wiki-page, as: page, effect: reads, facts: [Title]}
  contexts:
    web:
      place: web::workspace::wiki-page
- text: The Product moves the page to the trash and moves its children up to its parent
  kind: product
  actor: user
  entities:
  - {entity: wiki-page, as: page, effect: changes, from: Live, to: Trashed, facts: [Trashed at]}
  - {entity: wiki-page, as: child, effect: changes, facts: [Parent page]}
  contexts:
    web:
      place: web::workspace::wiki-page
---

# Move a page to the trash

## Trigger

A page is obsolete.

## Outcome

The page is out of the tree and search, restorable for 30 days.

## Edge cases

- Asking for the whole subtree trashes the children too, as one batch restored together.
