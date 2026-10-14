---
kind: primary
routes:
  web: Web app
steps:
- text: The User opens the stale-page queue
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace::wiki
- text: The Product lists the visible pages that need re-verification
  kind: product
  actor: user
  entities:
  - {entity: wiki-page, effect: reads, facts: [Title, Slug, Status, Verified at, Freshness]}
  contexts:
    web:
      place: web::workspace::wiki
---

# See which pages need re-verifying

## Trigger

The User keeps the wiki trustworthy.

## Outcome

The User knows which pages to check next.
