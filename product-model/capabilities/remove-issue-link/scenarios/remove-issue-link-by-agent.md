---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent removes a link from the issue
  kind: actor
  actor: ai-agent
  entities:
  - {entity: issue-link, effect: reads, facts: [Type]}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product deletes the link
  kind: product
  actor: ai-agent
  entities:
  - {entity: issue-link, effect: removes}
  contexts:
    agent:
      place: mcp
---

# Remove an issue link through MCP

## Trigger

A dependency no longer holds.

## Outcome

Neither issue shows the link.
