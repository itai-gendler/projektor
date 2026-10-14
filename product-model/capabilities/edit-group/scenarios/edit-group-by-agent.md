---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent changes a group's name or description
  kind: actor
  actor: ai-agent
  entities:
  - {entity: group, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product saves the group
  kind: product
  actor: ai-agent
  entities:
  - {entity: group, effect: changes, facts: [Name, Description]}
  contexts:
    agent:
      place: mcp
---

# Edit a group through MCP

## Trigger

A group's purpose changes.

## Outcome

The group carries the new name or description.
