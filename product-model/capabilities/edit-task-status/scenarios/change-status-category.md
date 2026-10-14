---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent changes a task status's category from In progress to Done
  kind: actor
  actor: ai-agent
  entities:
  - {entity: task-status, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product saves the task status and moves every issue in it to the done state
  kind: product
  actor: ai-agent
  entities:
  - {entity: task-status, effect: changes, facts: [Category]}
  - {entity: issue, effect: changes, from: In progress, to: Done, facts: []}
  contexts:
    agent:
      place: mcp
---

# Change a status's category

## Trigger

A status was put in the wrong category.

## Outcome

The status and every issue in it count as done.
