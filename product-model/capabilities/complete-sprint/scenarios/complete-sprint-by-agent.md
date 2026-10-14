---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent completes the active sprint
  kind: actor
  actor: ai-agent
  entities:
  - {entity: sprint, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product marks the sprint completed
  kind: product
  actor: ai-agent
  entities:
  - {entity: sprint, effect: changes, from: Active, to: Completed, facts: []}
  contexts:
    agent:
      place: mcp
---

# An agent completes the active sprint

## Trigger

The sprint's time box ends.

## Outcome

The sprint is completed.
