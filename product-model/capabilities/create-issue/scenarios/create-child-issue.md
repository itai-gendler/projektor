---
kind: alternative
routes:
  agent: MCP
steps:
- text: The AI agent files an issue with an epic as its parent
  kind: actor
  actor: ai-agent
  entities:
  - {entity: issue, as: epic, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The epic is visible and fewer than five levels deep
  kind: condition
  actor: ai-agent
  entities:
  - {entity: issue, as: epic, effect: reads, facts: [Parent]}
  contexts:
    agent:
      place: mcp
- text: The Product creates the child issue under the epic
  kind: product
  actor: ai-agent
  entities:
  - {entity: issue, as: child, effect: creates, to: Backlog, facts: [Ref, Title, Parent, Author kind]}
  contexts:
    agent:
      place: mcp
---

# File an issue under an epic

## Trigger

An epic is broken into smaller issues.

## Outcome

The epic's rollup counts the new child.

## Edge cases

- A parent that would put the child more than five levels deep is refused.
