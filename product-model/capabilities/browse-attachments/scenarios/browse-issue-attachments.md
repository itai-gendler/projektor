---
kind: primary
routes:
  web: Web app
steps:
- text: The User looks at an issue's attachments
  kind: actor
  actor: user
  entities:
  - {entity: attachment, effect: reads, facts: []}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::issue
- text: The Product lists them with their kind, name and size
  kind: product
  actor: user
  entities:
  - {entity: issue, effect: reads, facts: []}
  - {entity: attachment, effect: reads, facts: [Kind, File name, Size, URL, Attached at]}
  contexts:
    web:
      place: web::workspace::issue
---

# List an issue's attachments

## Trigger

The User needs the material attached to an issue.

## Outcome

The User sees every attachment; an agent gets file metadata, the bytes come from the web app.
