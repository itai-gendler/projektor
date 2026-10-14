---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent discards their unsaved changes to a page
  kind: actor
  actor: ai-agent
  entities:
  - {entity: wiki-draft, effect: reads, facts: [Saved at]}
  contexts:
    agent:
      place: mcp
- text: The Product deletes the page draft
  kind: product
  actor: ai-agent
  entities:
  - {entity: wiki-draft, effect: removes}
  contexts:
    agent:
      place: mcp
---

# Discard a draft through MCP

## Trigger

The AI agent no longer wants an unsaved edit.

## Outcome

The page is shown as published.
