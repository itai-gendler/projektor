---
kind: primary
routes:
  web: Web app
steps:
- text: The User asks for a share link on an issue
  kind: actor
  actor: user
  entities:
  - {entity: issue, effect: reads, facts: [Title]}
  - {entity: share-link, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::issue
- text: The Product creates a share link that expires in three days and shows its address
  kind: product
  actor: user
  entities:
  - {entity: share-link, effect: creates, facts: [Expires at]}
  contexts:
    web:
      place: web::workspace::issue
---

# Create a share link

## Trigger

The User wants someone outside the workspace to see an issue.

## Outcome

The User has a link to pass on.
