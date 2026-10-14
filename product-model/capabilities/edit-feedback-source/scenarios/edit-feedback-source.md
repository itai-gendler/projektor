---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent changes a source's name or description
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp
- text: The Product saves the feedback source
  kind: product
  actor: ai-agent
  entities:
  - {entity: feedback-source, effect: changes, facts: [Name, Description]}
  - {entity: feedback, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# Edit a feedback source

## Trigger

A source's purpose changes.

## Outcome

The source carries the new name or description.

## Edge cases

- A revoked source cannot be changed.
