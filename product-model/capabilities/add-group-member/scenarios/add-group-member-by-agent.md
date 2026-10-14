---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent adds one of the members to a group
  kind: actor
  actor: ai-agent
  entities:
  - {entity: workspace-membership, effect: reads, facts: [Role]}
  - {entity: group, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product adds the member to the group; the projects it grants appear on the member's next request
  kind: product
  actor: ai-agent
  entities:
  - {entity: group, effect: changes, facts: [Members]}
  - {entity: project, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# Add a member to a group through MCP

## Trigger

A member needs the access a group carries.

## Outcome

The member sees the group's projects at the group's roles.

## Edge cases

- Someone who is not a member of the workspace cannot be added.
