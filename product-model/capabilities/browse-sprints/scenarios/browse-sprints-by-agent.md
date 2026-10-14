---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent opens the sprints
  kind: actor
  actor: ai-agent
  entities:
  - {entity: sprint, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product lists the sprints in creation order with their status, dates and goals
  kind: product
  actor: ai-agent
  entities:
  - {entity: sprint, effect: reads, facts: [Name, Goal, Start date, End date]}
  contexts:
    agent:
      place: mcp
---

# Browse a project's sprints through MCP

## Trigger

The AI agent wants to see the project's cadence.

## Outcome

The AI agent sees every sprint of the project.

## Edge cases

- A project the actor cannot see lists no sprints.
