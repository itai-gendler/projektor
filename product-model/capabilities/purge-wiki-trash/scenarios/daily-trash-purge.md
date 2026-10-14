---
kind: unattended
routes:
  agent: MCP
steps:
- text: A day passes
  kind: condition
  unattended: true
  entities: []
  contexts:
    agent:
      place: mcp
- text: The Product removes, in every workspace, the pages trashed for at least 30 days with their revisions and attachments
  kind: product
  entities:
  - {entity: wiki-page, effect: removes, from: Trashed}
  - {entity: wiki-revision, effect: removes, with: wiki-page}
  - {entity: attachment, effect: removes, with: wiki-page}
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# Daily purge of expired trash

## Trigger

The daily schedule runs.

## Outcome

No page stays in any trash much longer than 30 days.
