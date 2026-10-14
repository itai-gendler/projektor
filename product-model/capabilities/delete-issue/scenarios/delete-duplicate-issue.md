---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent deletes a cancelled duplicate issue
  kind: actor
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product deletes the issue with its comments, links and share links and frees any children it had
  kind: product
  actor: ai-agent
  entities:
  - {entity: issue, effect: removes, from: Cancelled}
  - {entity: comment, effect: removes, with: issue}
  - {entity: share-link, effect: removes, with: issue}
  contexts:
    agent:
      place: mcp
---

# Delete a cancelled duplicate

## Trigger

An issue was filed twice.

## Outcome

The duplicate is gone for good.

## Edge cases

- An issue in any state can be deleted.
- A member with only a Member grant on the project is refused.
