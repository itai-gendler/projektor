---
kind: edge
routes:
  agent: MCP
steps:
- text: The AI agent claims paths one of which another live claim holds
  kind: actor
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: A live claim holds at least one requested path
  kind: condition
  actor: ai-agent
  entities:
  - {entity: file-claim, effect: reads, facts: [Path]}
  contexts:
    agent:
      place: mcp
- text: The Product claims nothing, records each contended path as a claim conflict, and answers naming the holding issue and agent
  kind: product
  actor: ai-agent
  entities:
  - {entity: claim-conflict, effect: reads, facts: []}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# A held path refuses the whole claim

## Trigger

Two agents working different issues reach for the same file.

## Outcome

Nothing is claimed; the holder is not told, and the agent can message it to negotiate.

## Edge cases

- If the holding issue is in a project the claimer cannot see, the answer does not name it.
