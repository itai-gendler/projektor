---
kind: alternative
routes:
  agent: MCP
steps:
- text: The AI agent moves a backlog issue to To do
  kind: actor
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product moves the issue and stamps when it became ready
  kind: product
  actor: ai-agent
  entities:
  - {entity: issue, effect: changes, from: Backlog, to: To do, facts: [Ready at]}
  contexts:
    agent:
      place: mcp
---

# An agent triages an issue out of the backlog

## Trigger

A groomed issue is ready to be worked.

## Outcome

The issue is open for work and its lead time has started.
