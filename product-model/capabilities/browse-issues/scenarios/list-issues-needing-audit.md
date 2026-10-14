---
kind: alternative
routes:
  agent: MCP
steps:
- text: The AI agent lists issues flagged as needing audit
  kind: actor
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product returns the visible issues an agent closed with evidence nothing external can check
  kind: product
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: [Ref, Title, Completion report, Needs audit]}
  contexts:
    agent:
      place: mcp
references:
- kind: code
  role: implementation
  target: apps/api/src/services/evidence-classification.ts
---

# List agent closures flagged for audit

## Trigger

A reviewer periodically checks how agents closed their work.

## Outcome

The AI agent has the queue of closures to review.
