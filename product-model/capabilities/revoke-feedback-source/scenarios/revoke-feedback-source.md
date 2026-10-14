---
kind: primary
routes:
  web: Web app
steps:
- text: The User revokes a feedback source
  kind: actor
  actor: user
  entities:
  - {entity: feedback-source, effect: reads, facts: [Name]}
  - {entity: feedback, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::feedback-source
- text: The Product revokes the source for good
  kind: product
  actor: user
  entities:
  - {entity: feedback-source, effect: changes, from: Active, to: Revoked, facts: [Revoked at]}
  contexts:
    web:
      place: web::workspace::feedback-source
---

# Revoke a source

## Trigger

An integration is retired.

## Outcome

The source's token is dead forever; a replacement needs a new source.

## Edge cases

- A paused source can be revoked too.
