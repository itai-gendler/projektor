---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent sets a planned sprint's status to active
  kind: actor
  actor: ai-agent
  entities:
  - {entity: sprint, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product saves the sprint as active
  kind: product
  actor: ai-agent
  entities:
  - {entity: sprint, effect: changes, from: Planned, to: Active, facts: []}
  contexts:
    agent:
      place: mcp
---

# An agent starts a sprint

## Trigger

A planned sprint begins.

## Outcome

The sprint is active.
