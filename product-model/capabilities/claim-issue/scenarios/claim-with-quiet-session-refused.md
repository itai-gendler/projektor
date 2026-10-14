---
kind: validation
routes:
  agent: MCP
steps:
- text: The AI agent claims an issue with a session silent for more than 120 seconds
  kind: actor
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The agent session is ended or has not been heard from within 120 seconds
  kind: condition
  actor: ai-agent
  entities:
  - {entity: agent-session, effect: reads, facts: [Last heartbeat]}
  contexts:
    agent:
      place: mcp
- text: The Product refuses the claim and asks for a heartbeat first
  kind: product
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp
---

# A quiet session cannot claim

## Trigger

An agent resumes after going quiet.

## Outcome

The agent must heartbeat before it can claim.
