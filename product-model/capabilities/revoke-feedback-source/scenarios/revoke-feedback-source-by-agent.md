---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent revokes a feedback source
  kind: actor
  actor: ai-agent
  entities:
  - {entity: feedback-source, effect: reads, facts: [Name]}
  - {entity: feedback, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product revokes the source for good
  kind: product
  actor: ai-agent
  entities:
  - {entity: feedback-source, effect: changes, from: Active, to: Revoked, facts: [Revoked at]}
  contexts:
    agent:
      place: mcp
---

# Revoke a source through MCP

## Trigger

An integration is retired.

## Outcome

The source's token is dead forever; a replacement needs a new source.

## Edge cases

- A paused source can be revoked too.
