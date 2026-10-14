---
kind: edge
routes:
  link: Share link
steps:
- text: The Link visitor opens a share link
  kind: actor
  actor: link-visitor
  entities:
  - {entity: share-link, effect: reads, facts: []}
  contexts:
    link:
      place: web::shared-link::shared-issue
- text: The link has expired, its issue was deleted, its project is archived, or its creator can no longer see the project
  kind: condition
  actor: link-visitor
  entities:
  - {entity: share-link, effect: reads, facts: [Expires at]}
  - {entity: project, effect: reads, facts: []}
  - {entity: user, effect: reads, facts: []}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    link:
      place: web::shared-link::shared-issue
- text: The Product answers that the link was not found or has expired
  kind: product
  actor: link-visitor
  entities: []
  contexts:
    link:
      place: web::shared-link::shared-issue
---

# A dead share link shows nothing

## Trigger

A share link outlives what made it valid.

## Outcome

Nothing about the issue is shown.
