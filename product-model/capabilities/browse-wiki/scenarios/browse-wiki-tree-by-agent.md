---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent opens the wiki's page tree
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp
- text: The Product lists the live pages the actor can see, nested under their parents
  kind: product
  actor: ai-agent
  entities:
  - {entity: wiki-page, effect: reads, facts: [Title, Slug, Parent page, Project]}
  contexts:
    agent:
      place: mcp
---

# Browse the page tree through MCP

## Trigger

The AI agent looks for a page by where it sits.

## Outcome

The AI agent sees the visible pages in their hierarchy.
