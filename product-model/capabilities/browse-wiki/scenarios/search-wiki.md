---
kind: alternative
routes:
  web: Web app
steps:
- text: The User searches the wiki for words
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace::wiki
- text: The Product returns matching live pages ranked with titles above bodies, each with a highlighted snippet and its freshness
  kind: product
  actor: user
  entities:
  - {entity: wiki-page, effect: reads, facts: [Title, Slug, Freshness]}
  contexts:
    web:
      place: web::workspace::wiki
---

# Search the wiki

## Trigger

The User remembers what a page said but not where it is.

## Outcome

The User finds matching pages from the projects they can see.
