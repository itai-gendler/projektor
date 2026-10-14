---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent restores a trashed page by its id
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp
- text: The Product brings the page back from the trash with the pages trashed in the same batch
  kind: product
  actor: ai-agent
  entities:
  - {entity: wiki-page, effect: changes, from: Trashed, to: Live, facts: [Trashed at]}
  contexts:
    agent:
      place: mcp
---

# An agent restores a trashed page

## Trigger

A page was trashed by mistake.

## Outcome

The page is live again.
