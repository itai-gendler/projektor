---
kind: validation
routes:
  agent: MCP
steps:
- text: The AI agent deletes a task status some issue is in
  kind: actor
  actor: ai-agent
  entities:
  - {entity: task-status, effect: reads, facts: []}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: An issue is in the task status, or it is the default
  kind: condition
  actor: ai-agent
  entities:
  - {entity: task-status, effect: reads, facts: [Default]}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product refuses the deletion as a conflict
  kind: product
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp
---

# Deleting a status in use is refused

## Trigger

Someone tries to remove a status still in use.

## Outcome

The status stays.
