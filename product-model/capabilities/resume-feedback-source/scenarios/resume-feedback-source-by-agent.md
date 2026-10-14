---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent resumes a paused feedback source
  kind: actor
  actor: ai-agent
  entities:
  - {entity: feedback-source, effect: reads, facts: [Name]}
  - {entity: feedback, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product makes the source active again
  kind: product
  actor: ai-agent
  entities:
  - {entity: feedback-source, effect: changes, from: Paused, to: Active, facts: []}
  contexts:
    agent:
      place: mcp
---

# Resume a source through MCP

## Trigger

The problem with a paused source is solved.

## Outcome

The source accepts feedback again with its existing token.
