---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent watches a page including the pages beneath it
  kind: actor
  actor: ai-agent
  entities:
  - {entity: wiki-page, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product records the page watch for the agent's person
  kind: product
  actor: ai-agent
  entities:
  - {entity: wiki-watch, effect: creates, facts: [Include subtree]}
  contexts:
    agent:
      place: mcp
---

# Watch a page and its subtree

## Trigger

Someone needs to keep up with a section of the wiki.

## Outcome

Changes there produce watch notifications for that person.

## Edge cases

- Watching a page already watched updates whether the subtree counts.
