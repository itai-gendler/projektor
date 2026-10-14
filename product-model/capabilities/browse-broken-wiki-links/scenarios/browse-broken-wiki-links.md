---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent lists the wiki's broken links
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp
- text: The Product returns each unresolved link with the page it sits on
  kind: product
  actor: ai-agent
  entities:
  - {entity: wiki-page, effect: reads, facts: [Title]}
  contexts:
    agent:
      place: mcp
---

# List broken links

## Trigger

Someone tends the wiki.

## Outcome

They have a queue of links to fix or pages to write.
