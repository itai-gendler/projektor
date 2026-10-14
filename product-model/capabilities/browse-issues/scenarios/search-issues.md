---
kind: alternative
routes:
  web: Web app
steps:
- text: The User types a keyword into the search box
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace::issues
- text: The Product returns issues from visible projects whose title or body matches, with an issue whose label equals the whole query listed first
  kind: product
  actor: user
  entities:
  - {entity: issue, effect: reads, facts: [Ref, Title, Labels]}
  - {entity: project, effect: reads, facts: [Key]}
  contexts:
    web:
      place: web::workspace::issues
---

# Search issues by keyword

## Trigger

The User remembers a word from an issue but not its ref.

## Outcome

The User finds matching issues only from projects they can see.
