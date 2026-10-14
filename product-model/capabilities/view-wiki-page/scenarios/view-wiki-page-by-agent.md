---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent opens a page
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp
- text: The Product shows the page's content, frontmatter and verification
  kind: product
  actor: ai-agent
  entities:
  - {entity: wiki-page, effect: reads, facts: [Title, Content, Type, Status, Tags, Verified at, Verified by, Freshness]}
  contexts:
    agent:
      place: mcp
---

# Read a page through MCP

## Trigger

The AI agent needs what the page says.

## Outcome

The AI agent reads the page; a long page reaches an agent in windows it can page through.
