---
kind: alternative
routes:
  agent: MCP
steps:
- text: The AI agent asks for the prioritized issues including those that are not ready
  kind: actor
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product includes them, each marked as needing grooming with the criteria it misses
  kind: product
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: [Ref, Definition of ready]}
  contexts:
    agent:
      place: mcp
---

# Include issues that are not ready, for grooming

## Trigger

Someone grooms the backlog.

## Outcome

The AI agent sees which issues miss acceptance criteria or scope.
