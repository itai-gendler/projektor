---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent deletes a group
  kind: actor
  actor: ai-agent
  entities:
  - {entity: group, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product deletes the group and its project grants
  kind: product
  actor: ai-agent
  entities:
  - {entity: group, effect: removes}
  - {entity: project-grant, effect: removes, with: group}
  - {entity: project, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# Delete a group through MCP

## Trigger

A group is no longer needed.

## Outcome

The group is gone and its grants no longer give anyone access.
