---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent sends a heartbeat for its session
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp
- text: The Product records that the agent session was heard from now
  kind: product
  actor: ai-agent
  entities:
  - {entity: agent-session, effect: changes, facts: [Last heartbeat]}
  contexts:
    agent:
      place: mcp
---

# Keep a session live

## Trigger

An agent works for a while without any other call that names its session.

## Outcome

The session stays live for another 120 seconds.
