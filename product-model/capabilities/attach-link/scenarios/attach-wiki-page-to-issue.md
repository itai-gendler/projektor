---
kind: primary
routes:
  web: Web app
steps:
- text: The User attaches a page of the wiki by its title
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace::issue
- text: The Product attaches a reference to the page
  kind: product
  actor: user
  entities:
  - {entity: issue, effect: reads, facts: []}
  - {entity: attachment, effect: creates, facts: [Kind, Attached at]}
  contexts:
    web:
      place: web::workspace::issue
---

# Attach a wiki page to an issue

## Trigger

An issue's background lives in the wiki.

## Outcome

The issue links to the page, which still resolves after a rename.
