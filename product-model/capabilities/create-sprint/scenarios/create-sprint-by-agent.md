---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent names a sprint and optionally gives it a goal and dates
  kind: actor
  actor: ai-agent
  entities:
  - {entity: sprint, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product creates the sprint as planned
  kind: product
  actor: ai-agent
  entities:
  - {entity: sprint, effect: creates, to: Planned, facts: [Name, Goal, Start date, End date]}
  contexts:
    agent:
      place: mcp
---

# Plan a sprint through MCP

## Trigger

The AI agent plans the next time box.

## Outcome

A planned sprint exists.
