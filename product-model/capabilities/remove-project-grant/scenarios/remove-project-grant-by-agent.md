---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent removes a project from a group
  kind: actor
  actor: ai-agent
  entities:
  - {entity: project, effect: reads, facts: [Name]}
  - {entity: group, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product deletes the project grant; members with no other grant on the project no longer find it
  kind: product
  actor: ai-agent
  entities:
  - {entity: project-grant, effect: removes}
  - {entity: project, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# Remove a group's project grant through MCP

## Trigger

A group's members should no longer reach a project.

## Outcome

The project is hidden from members who had it only through this group.
