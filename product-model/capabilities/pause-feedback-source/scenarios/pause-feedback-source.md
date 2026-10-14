---
kind: primary
routes:
  web: Web app
steps:
- text: The User pauses a feedback source
  kind: actor
  actor: user
  entities:
  - {entity: feedback-source, effect: reads, facts: [Name]}
  - {entity: feedback, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::feedback-source
- text: The Product pauses the source; submissions with its token are refused from now on
  kind: product
  actor: user
  entities:
  - {entity: feedback-source, effect: changes, from: Active, to: Paused, facts: []}
  contexts:
    web:
      place: web::workspace::feedback-source
---

# Pause a source

## Trigger

A source is being spammed or is misconfigured.

## Outcome

The source refuses feedback until it is resumed.
