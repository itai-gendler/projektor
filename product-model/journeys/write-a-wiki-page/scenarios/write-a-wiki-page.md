---
kind: primary
result: achieved
routes:
  web: Web app
steps:
- text: The User creates a page with a title and a first draft
  kind: actor
  actor: user
  entities: []
  capability: create-wiki-page
  contexts:
    web:
      place: web::workspace::wiki
- text: The Product creates the page and opens it
  kind: product
  actor: user
  entities:
  - {entity: wiki-page, effect: creates, to: Live, facts: [Title, Slug, Content]}
  capability: create-wiki-page
  contexts:
    web:
      place: web::workspace::wiki
- text: The User edits the new page's content and saves
  kind: actor
  actor: user
  entities:
  - {entity: wiki-page, effect: reads, facts: [Title, Content]}
  capability: edit-wiki-page
  contexts:
    web:
      place: web::workspace::wiki-page
- text: The Product keeps the first draft as a page revision and saves the page
  kind: product
  actor: user
  entities:
  - {entity: wiki-revision, effect: creates, facts: [Content, Title, Author, Saved at]}
  - {entity: wiki-page, effect: changes, facts: [Content]}
  capability: edit-wiki-page
  contexts:
    web:
      place: web::workspace::wiki-page
---

# Create a page and keep editing it

## Trigger

A member creates a page from the wiki.

## Outcome

The member lands on the new page and refines it there.
