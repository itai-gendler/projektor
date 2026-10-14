---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent confirms rotating a feedback source's token
  kind: actor
  actor: ai-agent
  entities:
  - {entity: feedback-source, effect: reads, facts: [Name]}
  - {entity: feedback, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product issues a new submit token, shows it once and stops accepting the old one
  kind: product
  actor: ai-agent
  entities:
  - {entity: feedback-source, effect: changes, facts: [Submit token]}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# Rotate a leaked token through MCP

## Trigger

A source's token leaked.

## Outcome

Only the new token submits to the source.

## Edge cases

- A revoked source cannot be rotated.
