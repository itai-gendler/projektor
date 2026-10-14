---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent picks a project and a role for a group
  kind: actor
  actor: ai-agent
  entities:
  - {entity: project, effect: reads, facts: [Name]}
  - {entity: group, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product gives the group a project grant with that role
  kind: product
  actor: ai-agent
  entities:
  - {entity: project-grant, effect: creates, facts: [Role]}
  - {entity: project, effect: reads, facts: []}
  - {entity: group, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# Grant a project to a group through MCP

## Trigger

A group's members need to work in a project.

## Outcome

The group's members see the project at the granted role from their next request.
