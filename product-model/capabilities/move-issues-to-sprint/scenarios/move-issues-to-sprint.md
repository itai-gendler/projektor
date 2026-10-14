---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent moves a set of issues into a sprint by ref
  kind: actor
  actor: ai-agent
  entities:
  - {entity: sprint, effect: reads, facts: [Name]}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product plans every issue into the sprint
  kind: product
  actor: ai-agent
  entities:
  - {entity: issue, effect: changes, facts: [Sprint]}
  - {entity: sprint, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# Plan issues into a sprint

## Trigger

Sprint planning decides what goes into the sprint.

## Outcome

The issues are planned into the sprint.
