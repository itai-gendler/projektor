---
kind: validation
routes:
  agent: MCP
steps:
- text: The AI agent finishes with a completion report but no status that hands the issue in
  kind: actor
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The issue is neither moving into review or done nor already there
  kind: condition
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product refuses before changing anything, so the agent session stays live to retry
  kind: product
  actor: ai-agent
  entities:
  - {entity: agent-session, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# A report without a move into review or done is refused

## Trigger

An agent files a report at the wrong moment.

## Outcome

Nothing changes; the agent can try again.
