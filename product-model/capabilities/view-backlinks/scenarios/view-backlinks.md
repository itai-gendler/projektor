---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent asks which pages link to a page
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp
- text: The Product returns the visible linking pages with a snippet of the citing text
  kind: product
  actor: ai-agent
  entities:
  - {entity: wiki-page, effect: reads, facts: [Title, Slug]}
  contexts:
    agent:
      place: mcp
---

# See what links to a page

## Trigger

Someone is about to change or delete a page.

## Outcome

They know which pages depend on it.
