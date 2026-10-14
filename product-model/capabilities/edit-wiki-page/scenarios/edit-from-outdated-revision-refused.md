---
kind: edge
routes:
  agent: MCP
steps:
- text: The AI agent saves a page naming the revision it read
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp
- text: Someone else saved the page since that revision
  kind: condition
  actor: ai-agent
  entities:
  - {entity: wiki-revision, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product refuses the save as a conflict and asks the agent to read again
  kind: product
  actor: ai-agent
  entities:
  - {entity: wiki-page, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# A save from an outdated revision is refused

## Trigger

Two writers edit the same page at once.

## Outcome

Neither write is silently lost.

## Edge cases

- A save that names no base revision overwrites whatever is there.
