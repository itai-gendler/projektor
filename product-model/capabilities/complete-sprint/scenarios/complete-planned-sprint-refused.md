---
kind: validation
routes:
  agent: MCP
steps:
- text: The AI agent asks to complete a sprint that is still planned
  kind: actor
  actor: ai-agent
  entities:
  - {entity: sprint, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The sprint is not active
  kind: condition
  actor: ai-agent
  entities:
  - {entity: sprint, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: 'The Product refuses: only active sprints can be completed'
  kind: product
  actor: ai-agent
  entities:
  - {entity: sprint, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# Completing a sprint that is not active is refused

## Trigger

An agent tries to complete a sprint that never started.

## Outcome

The sprint keeps its status.
