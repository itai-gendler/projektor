---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent marks all its person's watch notifications read
  kind: actor
  actor: ai-agent
  entities:
  - {entity: wiki-notification, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product marks every unread watch notification read
  kind: product
  actor: ai-agent
  entities:
  - {entity: wiki-notification, effect: changes, from: Unread, to: Read, facts: []}
  contexts:
    agent:
      place: mcp
---

# Mark everything read

## Trigger

Someone has caught up.

## Outcome

No notification is left unread.
