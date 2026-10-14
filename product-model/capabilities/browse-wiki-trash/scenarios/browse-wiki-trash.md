---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent lists the wiki trash
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp
- text: The Product returns the trashed pages with their ids for restoring
  kind: product
  actor: ai-agent
  entities:
  - {entity: wiki-page, effect: reads, facts: [Title, Trashed at]}
  contexts:
    agent:
      place: mcp
---

# See what is in the trash

## Trigger

Someone looks for a deleted page.

## Outcome

They can restore it by its id.
