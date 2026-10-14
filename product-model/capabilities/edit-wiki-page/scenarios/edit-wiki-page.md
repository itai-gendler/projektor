---
kind: primary
routes:
  web: Web app
steps:
- text: The User edits the page's content and saves
  kind: actor
  actor: user
  entities:
  - {entity: wiki-page, effect: reads, facts: [Title, Content]}
  contexts:
    web:
      place: web::workspace::wiki-page
- text: The Product keeps the previous content as a page revision and saves the page
  kind: product
  actor: user
  entities:
  - {entity: wiki-revision, effect: creates, facts: [Content, Title, Author, Saved at]}
  - {entity: wiki-page, effect: changes, facts: [Content, Type, Status, Tags]}
  contexts:
    web:
      place: web::workspace::wiki-page
---

# Edit a page

## Trigger

A page needs updating.

## Outcome

The page shows the new content and its history has the old one.
