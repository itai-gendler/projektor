---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent removes a member from a group
  kind: actor
  actor: ai-agent
  entities:
  - {entity: group, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product takes the member out of the group; access only it gave ends on their next request
  kind: product
  actor: ai-agent
  entities:
  - {entity: group, effect: changes, facts: [Members]}
  contexts:
    agent:
      place: mcp
---

# Remove a member from a group through MCP

## Trigger

A member should lose a group's access.

## Outcome

The member no longer sees projects only that group granted.
