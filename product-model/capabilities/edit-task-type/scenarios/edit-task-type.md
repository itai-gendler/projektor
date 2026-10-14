---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent renames a type and makes it the default
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp
- text: The Product saves the task type
  kind: product
  actor: ai-agent
  entities:
  - {entity: task-type, effect: changes, facts: [Name, Color, Icon, Position, Default]}
  contexts:
    agent:
      place: mcp
---

# Edit task type

## Trigger

The team's kinds of work change.

## Outcome

The type is updated.

## Edge cases

- Making a type the default takes the default from the previous one.
