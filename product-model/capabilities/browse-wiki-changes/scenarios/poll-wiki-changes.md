---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent asks for wiki changes since its last poll
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp
- text: The Product returns the changes to visible pages since then, and the moment to poll from next
  kind: product
  actor: ai-agent
  entities:
  - {entity: wiki-page, effect: reads, facts: [Title, Slug]}
  contexts:
    agent:
      place: mcp
---

# Poll for changes

## Trigger

An agent keeps its knowledge of the wiki current.

## Outcome

The AI agent knows what changed without re-reading everything.
