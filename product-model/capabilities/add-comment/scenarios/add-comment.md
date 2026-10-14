---
kind: primary
routes:
  web: Web app
steps:
- text: The User writes a comment on an issue
  kind: actor
  actor: user
  entities:
  - {entity: issue, effect: reads, facts: [Title]}
  - {entity: comment, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::issue
- text: The Product adds the comment, marked as written by a person or an agent according to how the actor signed in
  kind: product
  actor: user
  entities:
  - {entity: comment, effect: creates, facts: [Body, Author kind, Posted at]}
  contexts:
    web:
      place: web::workspace::issue
---

# Comment on an issue

## Trigger

The User has something to say about an issue.

## Outcome

The comment is on the issue's timeline.
