---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent lists active agent sessions
  kind: actor
  actor: ai-agent
  entities:
  - {entity: agent-session, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product returns the live sessions, each with the ref of the issue it is linked to
  kind: product
  actor: ai-agent
  entities:
  - {entity: agent-session, effect: reads, facts: [Name, Linked issue, Started at, Last heartbeat]}
  - {entity: issue, effect: reads, facts: [Ref]}
  contexts:
    agent:
      place: mcp
---

# See which agents are working

## Trigger

An agent wants to know who else is in the workspace.

## Outcome

The AI agent sees the live fleet.
