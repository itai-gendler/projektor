---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent gives a new page a title, an optional parent and its content
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp
- text: The Product creates the page with a slug from its title, indexes it for search and resolves links that were waiting for it
  kind: product
  actor: ai-agent
  entities:
  - {entity: wiki-page, effect: creates, to: Live, facts: [Title, Slug, Content, Parent page, Type, Status, Tags]}
  contexts:
    agent:
      place: mcp
---

# Create a page through MCP

## Trigger

The AI agent has knowledge worth keeping.

## Outcome

The page is live and searchable.

## Edge cases

- A slug another page uses, a reserved slug, or one shaped like an id is refused.
