---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent edits a comment it wrote
  kind: actor
  actor: ai-agent
  entities:
  - {entity: comment, effect: reads, facts: [Body]}
  contexts:
    agent:
      place: mcp
- text: The Product saves the new text
  kind: product
  actor: ai-agent
  entities:
  - {entity: comment, effect: changes, facts: [Body, Edited at]}
  contexts:
    agent:
      place: mcp
---

# Edit one's own comment through MCP

## Trigger

The AI agent wants to correct what they wrote.

## Outcome

The comment shows the new text.

## Edge cases

- Editing someone else's comment is refused, whatever the editor's role.
