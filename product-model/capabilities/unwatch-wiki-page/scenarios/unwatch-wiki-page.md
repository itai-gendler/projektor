---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent stops watching a page
  kind: actor
  actor: ai-agent
  entities:
  - {entity: wiki-page, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product deletes the page watch
  kind: product
  actor: ai-agent
  entities:
  - {entity: wiki-watch, effect: removes}
  contexts:
    agent:
      place: mcp
---

# Stop watching a page

## Trigger

A page no longer matters to someone.

## Outcome

No more notifications come from it.
