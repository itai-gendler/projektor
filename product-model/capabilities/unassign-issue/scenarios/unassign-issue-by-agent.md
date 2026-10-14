---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent clears the issue's assignee
  kind: actor
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product leaves the issue unassigned
  kind: product
  actor: ai-agent
  entities:
  - {entity: issue, effect: changes, facts: [Assignee]}
  contexts:
    agent:
      place: mcp
---

# Unassign an issue through MCP

## Trigger

An issue's owner steps away from it.

## Outcome

The issue has no assignee.
