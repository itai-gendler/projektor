---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent links the issue to another issue by ref with a link type
  kind: actor
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: [Title]}
  contexts:
    agent:
      place: mcp
- text: The Product records the link, shown from each issue's side with the matching type
  kind: product
  actor: ai-agent
  entities:
  - {entity: issue-link, effect: creates, facts: [Type]}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# Link two issues through MCP

## Trigger

The AI agent notices that two issues depend on each other.

## Outcome

Both issues show the link; blocked issues weigh into prioritization.
