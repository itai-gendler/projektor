---
kind: primary
routes:
  web: Web app
steps:
- text: The User opens the page's history and picks a revision
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace::wiki-page
- text: The Product lists the revisions and shows the difference between the chosen one and the current content
  kind: product
  actor: user
  entities:
  - {entity: wiki-revision, effect: reads, facts: [Title, Summary, Author, Saved at, Content]}
  - {entity: wiki-page, effect: reads, facts: [Content]}
  contexts:
    web:
      place: web::workspace::wiki-page
---

# Compare a revision with the current page

## Trigger

The User wants to know what changed on a page.

## Outcome

The User sees who changed what and when.
