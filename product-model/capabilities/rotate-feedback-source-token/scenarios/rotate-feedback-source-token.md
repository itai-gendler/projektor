---
kind: primary
routes:
  web: Web app
steps:
- text: The User confirms rotating a feedback source's token
  kind: actor
  actor: user
  entities:
  - {entity: feedback-source, effect: reads, facts: [Name]}
  - {entity: feedback, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::feedback-source
- text: The Product issues a new submit token, shows it once and stops accepting the old one
  kind: product
  actor: user
  entities:
  - {entity: feedback-source, effect: changes, facts: [Submit token]}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::feedback-source
---

# Rotate a leaked token

## Trigger

A source's token leaked.

## Outcome

Only the new token submits to the source.

## Edge cases

- A revoked source cannot be rotated.
