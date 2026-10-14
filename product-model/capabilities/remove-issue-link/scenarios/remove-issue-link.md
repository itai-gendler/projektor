---
kind: primary
routes:
  web: Web app
steps:
- text: The User removes a link from the issue
  kind: actor
  actor: user
  entities:
  - {entity: issue-link, effect: reads, facts: [Type]}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::issue
- text: The Product deletes the link
  kind: product
  actor: user
  entities:
  - {entity: issue-link, effect: removes}
  contexts:
    web:
      place: web::workspace::issue
---

# Remove an issue link

## Trigger

A dependency no longer holds.

## Outcome

Neither issue shows the link.
