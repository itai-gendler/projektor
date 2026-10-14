---
kind: primary
routes:
  web: Web app
steps:
- text: The User edits a comment it wrote
  kind: actor
  actor: user
  entities:
  - {entity: comment, effect: reads, facts: [Body]}
  contexts:
    web:
      place: web::workspace::issue
- text: The Product saves the new text
  kind: product
  actor: user
  entities:
  - {entity: comment, effect: changes, facts: [Body, Edited at]}
  contexts:
    web:
      place: web::workspace::issue
---

# Edit one's own comment

## Trigger

The User wants to correct what they wrote.

## Outcome

The comment shows the new text.

## Edge cases

- Editing someone else's comment is refused, whatever the editor's role.
