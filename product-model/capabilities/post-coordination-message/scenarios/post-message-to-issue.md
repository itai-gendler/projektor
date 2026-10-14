---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent posts a message to an issue's channel, naming its session
  kind: actor
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product keeps the coordination message and refreshes the session's heartbeat
  kind: product
  actor: ai-agent
  entities:
  - {entity: coordination-message, effect: creates, facts: [Channel, Body, Posted at]}
  - {entity: agent-session, effect: changes, facts: [Last heartbeat]}
  contexts:
    agent:
      place: mcp
---

# Message an issue's channel

## Trigger

An agent was refused a claim and wants to talk to the holder.

## Outcome

The message waits on the issue's channel.
