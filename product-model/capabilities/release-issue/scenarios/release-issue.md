---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent releases the lease its session holds on an issue
  kind: actor
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product releases the issue lease
  kind: product
  actor: ai-agent
  entities:
  - {entity: issue-lease, effect: changes, from: Held, to: Released, facts: [Released at, Release reason]}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# Release an issue

## Trigger

An agent stops working an issue without finishing it.

## Outcome

The issue is free for another agent.

## Edge cases

- Releasing an issue with no lease is answered as not found.
