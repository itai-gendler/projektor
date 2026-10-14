---
kind: alternative
routes:
  agent: MCP
steps:
- text: The AI agent sets a reviewed feedback item's status to actioned
  kind: actor
  actor: ai-agent
  entities:
  - {entity: feedback, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product saves the status
  kind: product
  actor: ai-agent
  entities:
  - {entity: feedback, effect: changes, from: Reviewed, to: Actioned, facts: []}
  contexts:
    agent:
      place: mcp
---

# An agent marks feedback actioned

## Trigger

Something was done about a piece of feedback.

## Outcome

The item is recorded as actioned.
