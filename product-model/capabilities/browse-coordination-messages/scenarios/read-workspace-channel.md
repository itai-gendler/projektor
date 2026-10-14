---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent lists the workspace channel's messages
  kind: actor
  actor: ai-agent
  entities:
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product returns the messages page by page
  kind: product
  actor: ai-agent
  entities:
  - {entity: coordination-message, effect: reads, facts: [Channel, Body, Posted at]}
  contexts:
    agent:
      place: mcp
---

# Read the workspace channel

## Trigger

An agent catches up on fleet-wide notices.

## Outcome

The AI agent has read the channel.
