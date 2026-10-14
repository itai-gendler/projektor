---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent lists its person's unread watch notifications
  kind: actor
  actor: ai-agent
  entities:
  - {entity: wiki-notification, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product returns them with the page and what happened to it
  kind: product
  actor: ai-agent
  entities:
  - {entity: wiki-notification, effect: reads, facts: [Page title, Page slug, Action, Notified at]}
  contexts:
    agent:
      place: mcp
---

# Read watch notifications

## Trigger

Someone catches up on the pages they follow.

## Outcome

They know which pages changed.
