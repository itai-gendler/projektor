---
kind: edge
routes:
  agent: MCP
steps:
- text: The AI agent claims an issue another live session holds
  kind: actor
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The holding agent session has been heard from within 120 seconds
  kind: condition
  actor: ai-agent
  entities:
  - {entity: agent-session, effect: reads, facts: [Last heartbeat]}
  - {entity: issue-lease, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product refuses the claim as a conflict naming the holding session
  kind: product
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp
---

# A live holder keeps the issue

## Trigger

Two agents reach for the same issue.

## Outcome

The first agent keeps the issue.
