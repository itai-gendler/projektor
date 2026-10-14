---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent deletes a planned sprint
  kind: actor
  actor: ai-agent
  entities:
  - {entity: sprint, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product takes every issue out of the sprint and deletes it
  kind: product
  actor: ai-agent
  entities:
  - {entity: issue, effect: changes, facts: [Sprint]}
  - {entity: sprint, effect: removes, from: Planned}
  contexts:
    agent:
      place: mcp
---

# Delete a sprint

## Trigger

A sprint was planned by mistake.

## Outcome

The sprint is gone and its issues are unplanned.

## Edge cases

- A sprint in any status can be deleted.
