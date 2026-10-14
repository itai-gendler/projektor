---
kind: alternative
routes:
  agent: MCP
steps:
- text: The AI agent picks a different role for a project the group already holds
  kind: actor
  actor: ai-agent
  entities:
  - {entity: project, effect: reads, facts: [Name]}
  - {entity: group, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product replaces the role on the existing project grant
  kind: product
  actor: ai-agent
  entities:
  - {entity: project-grant, effect: changes, facts: [Role]}
  - {entity: project, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# Change the role a group holds on a project through MCP

## Trigger

A group's members need more or less access to a project.

## Outcome

The group holds the project at the new role.
