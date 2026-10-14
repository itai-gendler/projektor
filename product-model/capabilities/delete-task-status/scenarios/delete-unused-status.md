---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent deletes a task status
  kind: actor
  actor: ai-agent
  entities:
  - {entity: task-status, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The task status is not the default and no issue is in it
  kind: condition
  actor: ai-agent
  entities:
  - {entity: task-status, effect: reads, facts: [Default]}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product deletes the task status
  kind: product
  actor: ai-agent
  entities:
  - {entity: task-status, effect: removes}
  contexts:
    agent:
      place: mcp
---

# Delete an unused status

## Trigger

A status is no longer part of the workflow.

## Outcome

The status is gone from the list.
