---
kind: primary
routes:
  web: Web app
steps:
- text: The User edits a page without publishing
  kind: actor
  actor: user
  entities:
  - {entity: wiki-page, effect: reads, facts: [Content]}
  contexts:
    web:
      place: web::workspace::wiki-page
- text: The Product keeps the edit as the actor's page draft, replacing any earlier draft of theirs for the page
  kind: product
  actor: user
  entities:
  - {entity: wiki-draft, effect: creates, facts: [Title, Content, Base revision, Saved at]}
  contexts:
    web:
      place: web::workspace::wiki-page
---

# Keep an unsaved edit

## Trigger

The User is part-way through an edit.

## Outcome

The draft can be picked up later, from any device; nobody else sees it.
