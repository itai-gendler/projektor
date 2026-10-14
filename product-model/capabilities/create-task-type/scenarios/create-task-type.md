---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent adds a Spike type
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp
- text: The Product adds the task type
  kind: product
  actor: ai-agent
  entities:
  - {entity: task-type, effect: creates, facts: [Key, Name, Color, Icon, Position, Default]}
  contexts:
    agent:
      place: mcp
---

# Create task type

## Trigger

The team's kinds of work change.

## Outcome

The type is offered for new issues.

## Edge cases

- A key the workspace already uses is refused.
- Making a type the default takes the default from the previous one.
