---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent changes the issue's title, body, priority or story points
  kind: actor
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: [Title, Body, Priority]}
  contexts:
    agent:
      place: mcp
- text: The Product saves the issue and re-checks its body against the definition of ready
  kind: product
  actor: ai-agent
  entities:
  - {entity: issue, effect: changes, facts: [Title, Body, Priority, Story points, Definition of ready]}
  contexts:
    agent:
      place: mcp
---

# Edit an issue's details through MCP

## Trigger

The AI agent refines what the issue says.

## Outcome

The issue shows the new details and readiness.
