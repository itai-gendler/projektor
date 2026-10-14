---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent names a new group and describes it
  kind: actor
  actor: ai-agent
  entities:
  - {entity: group, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product creates the group with no members and no project grants
  kind: product
  actor: ai-agent
  entities:
  - {entity: group, effect: creates, facts: [Name, Description, Members]}
  - {entity: project-grant, effect: reads, facts: []}
  - {entity: project, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# Create a group through MCP

## Trigger

The AI agent wants to give a set of people access to some projects.

## Outcome

An empty group exists, ready for members and grants.

## Edge cases

- A name another group in the workspace already uses is refused as a conflict.
