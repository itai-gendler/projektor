---
kind: alternative
routes:
  web: Web app
steps:
- text: The User picks a template for a new page
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace::wiki
- text: The Product creates the page in the project with the template's content
  kind: product
  actor: user
  entities:
  - {entity: project, effect: reads, facts: []}
  - {entity: wiki-page, effect: creates, to: Live, facts: [Title, Slug, Content, Project]}
  contexts:
    web:
      place: web::workspace::wiki
references:
- kind: code
  role: implementation
  target: apps/api/src/services/wiki.ts#listWikiTemplates
---

# Create a page from a template

## Trigger

The User writes a runbook or decision record.

## Outcome

The page starts from the template's structure.
