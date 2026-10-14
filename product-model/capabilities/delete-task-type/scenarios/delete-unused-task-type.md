---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent deletes a task type
  kind: actor
  actor: ai-agent
  entities:
  - {entity: task-type, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: No issue is of the task type
  kind: condition
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: [Type]}
  - {entity: task-type, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product deletes the task type
  kind: product
  actor: ai-agent
  entities:
  - {entity: task-type, effect: removes}
  contexts:
    agent:
      place: mcp
---

# Delete an unused type

## Trigger

A type is no longer used.

## Outcome

The type is gone from the list.

## Edge cases

- A type some issue still has is refused as a conflict.
