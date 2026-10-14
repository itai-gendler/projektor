---
kind: primary
routes:
  web: Web app
steps:
- text: The User discards their unsaved changes to a page
  kind: actor
  actor: user
  entities:
  - {entity: wiki-draft, effect: reads, facts: [Saved at]}
  contexts:
    web:
      place: web::workspace::wiki-page
- text: The Product deletes the page draft
  kind: product
  actor: user
  entities:
  - {entity: wiki-draft, effect: removes}
  contexts:
    web:
      place: web::workspace::wiki-page
---

# Discard a draft

## Trigger

The User no longer wants an unsaved edit.

## Outcome

The page is shown as published.
