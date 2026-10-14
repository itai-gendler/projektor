---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent opens the feedback sources
  kind: actor
  actor: ai-agent
  entities:
  - {entity: feedback-source, effect: reads, facts: []}
  - {entity: feedback, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product lists the sources with their state and a summary of their feedback
  kind: product
  actor: ai-agent
  entities:
  - {entity: feedback-source, effect: reads, facts: [Name, Description, Allowed origins, Created at]}
  - {entity: feedback, effect: reads, facts: [Rating, Received at]}
  contexts:
    agent:
      place: mcp
---

# Browse a project's feedback sources through MCP

## Trigger

The AI agent checks how feedback collection is going.

## Outcome

The AI agent sees each source and what it has received.
