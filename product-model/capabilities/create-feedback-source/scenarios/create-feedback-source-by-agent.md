---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent names a new feedback source and optionally lists the origins its widget runs on
  kind: actor
  actor: ai-agent
  entities:
  - {entity: feedback-source, effect: reads, facts: []}
  - {entity: feedback, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product creates the active source and shows its submit token once
  kind: product
  actor: ai-agent
  entities:
  - {entity: feedback-source, effect: creates, to: Active, facts: [Name, Description, Allowed origins, Submit token, Created at]}
  contexts:
    agent:
      place: mcp
---

# Create a feedback source through MCP

## Trigger

The AI agent wants to collect feedback from a product's users.

## Outcome

The source accepts feedback through the token, which is never shown again.
