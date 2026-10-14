---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent pauses a feedback source
  kind: actor
  actor: ai-agent
  entities:
  - {entity: feedback-source, effect: reads, facts: [Name]}
  - {entity: feedback, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product pauses the source; submissions with its token are refused from now on
  kind: product
  actor: ai-agent
  entities:
  - {entity: feedback-source, effect: changes, from: Active, to: Paused, facts: []}
  contexts:
    agent:
      place: mcp
---

# Pause a source through MCP

## Trigger

A source is being spammed or is misconfigured.

## Outcome

The source refuses feedback until it is resumed.
