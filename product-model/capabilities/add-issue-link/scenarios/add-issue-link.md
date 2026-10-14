---
kind: primary
routes:
  web: Web app
steps:
- text: The User links the issue to another issue by ref with a link type
  kind: actor
  actor: user
  entities:
  - {entity: issue, effect: reads, facts: [Title]}
  contexts:
    web:
      place: web::workspace::issue
- text: The Product records the link, shown from each issue's side with the matching type
  kind: product
  actor: user
  entities:
  - {entity: issue-link, effect: creates, facts: [Type]}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::issue
---

# Link two issues

## Trigger

The User notices that two issues depend on each other.

## Outcome

Both issues show the link; blocked issues weigh into prioritization.
