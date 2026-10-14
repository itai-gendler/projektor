---
kind: primary
routes:
  web: Web app
steps:
- text: The User removes an attachment from an issue
  kind: actor
  actor: user
  entities:
  - {entity: attachment, effect: reads, facts: [File name]}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::issue
- text: The Product deletes the attachment and its stored file
  kind: product
  actor: user
  entities:
  - {entity: issue, effect: reads, facts: []}
  - {entity: attachment, effect: removes}
  contexts:
    web:
      place: web::workspace::issue
---

# Remove an attachment

## Trigger

An attachment is out of date.

## Outcome

It is no longer listed and its file is gone.
