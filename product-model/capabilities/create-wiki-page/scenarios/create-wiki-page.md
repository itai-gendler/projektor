---
kind: primary
routes:
  web: Web app
steps:
- text: The User gives a new page a title, an optional parent and its content
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace::wiki
- text: The Product creates the page with a slug from its title, indexes it for search and resolves links that were waiting for it
  kind: product
  actor: user
  entities:
  - {entity: wiki-page, effect: creates, to: Live, facts: [Title, Slug, Content, Parent page, Type, Status, Tags]}
  contexts:
    web:
      place: web::workspace::wiki
---

# Create a page

## Trigger

The User has knowledge worth keeping.

## Outcome

The page is live and searchable.

## Edge cases

- A slug another page uses, a reserved slug, or one shaped like an id is refused.
