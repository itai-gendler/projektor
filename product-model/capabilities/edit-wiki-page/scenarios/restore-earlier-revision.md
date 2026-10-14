---
kind: alternative
routes:
  web: Web app
steps:
- text: The User picks an earlier revision in the page's history and restores it
  kind: actor
  actor: user
  entities:
  - {entity: wiki-revision, effect: reads, facts: [Content, Saved at]}
  contexts:
    web:
      place: web::workspace::wiki-page
- text: The Product saves the revision's content as the page's content, keeping the replaced content as a new revision
  kind: product
  actor: user
  entities:
  - {entity: wiki-revision, effect: creates, facts: [Content, Title, Author, Saved at]}
  - {entity: wiki-page, effect: changes, facts: [Content]}
  contexts:
    web:
      place: web::workspace::wiki-page
---

# Bring back an earlier revision

## Trigger

A change to a page turns out wrong.

## Outcome

The page reads as it did, and nothing is lost from its history.
