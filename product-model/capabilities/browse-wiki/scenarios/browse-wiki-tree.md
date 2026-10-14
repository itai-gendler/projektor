---
kind: primary
routes:
  web: Web app
steps:
- text: The User opens the wiki's page tree
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace::wiki
- text: The Product lists the live pages the actor can see, nested under their parents
  kind: product
  actor: user
  entities:
  - {entity: wiki-page, effect: reads, facts: [Title, Slug, Parent page, Project]}
  contexts:
    web:
      place: web::workspace::wiki
---

# Browse the page tree

## Trigger

The User looks for a page by where it sits.

## Outcome

The User sees the visible pages in their hierarchy.
