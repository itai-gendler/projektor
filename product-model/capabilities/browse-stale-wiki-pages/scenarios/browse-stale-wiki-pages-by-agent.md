---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent opens the stale-page queue
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp
- text: The Product lists the visible pages that need re-verification
  kind: product
  actor: ai-agent
  entities:
  - {entity: wiki-page, effect: reads, facts: [Title, Slug, Status, Verified at, Freshness]}
  contexts:
    agent:
      place: mcp
---

# See which pages need re-verifying through MCP

## Trigger

The AI agent keeps the wiki trustworthy.

## Outcome

The AI agent knows which pages to check next.
