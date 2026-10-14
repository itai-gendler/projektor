---
kind: primary
routes:
  web: Web app
steps:
- text: The User deletes a comment
  kind: actor
  actor: user
  entities:
  - {entity: comment, effect: reads, facts: [Body]}
  contexts:
    web:
      place: web::workspace::issue
- text: The Product removes the comment
  kind: product
  actor: user
  entities:
  - {entity: comment, effect: removes}
  contexts:
    web:
      place: web::workspace::issue
---

# Delete a comment

## Trigger

A comment should not stay on the issue.

## Outcome

The comment is gone.
