---
kind: alternative
routes:
  agent: MCP
steps:
- text: The AI agent sends a heartbeat after more than 120 seconds of silence
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp
- text: The session was never ended
  kind: condition
  actor: ai-agent
  entities:
  - {entity: agent-session, effect: reads, facts: [Last heartbeat, Ended at]}
  contexts:
    agent:
      place: mcp
- text: The Product records the heartbeat and the session is live again
  kind: product
  actor: ai-agent
  entities:
  - {entity: agent-session, effect: changes, facts: [Last heartbeat]}
  contexts:
    agent:
      place: mcp
---

# A quiet session comes back to life

## Trigger

An agent was busy and went quiet.

## Outcome

The session can claim again; anything another agent reclaimed meanwhile stays reclaimed.
