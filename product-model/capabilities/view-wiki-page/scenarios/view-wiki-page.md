---
kind: primary
routes:
  web: Web app
steps:
- text: The User opens a page
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace::wiki-page
- text: The Product shows the page's content, frontmatter and verification
  kind: product
  actor: user
  entities:
  - {entity: wiki-page, effect: reads, facts: [Title, Content, Type, Status, Tags, Verified at, Verified by, Freshness]}
  contexts:
    web:
      place: web::workspace::wiki-page
---

# Read a page

## Trigger

The User needs what the page says.

## Outcome

The User reads the page; a long page reaches an agent in windows it can page through.
