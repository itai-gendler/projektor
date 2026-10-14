---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent removes an attachment from an issue
  kind: actor
  actor: ai-agent
  entities:
  - {entity: attachment, effect: reads, facts: [File name]}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product deletes the attachment and its stored file
  kind: product
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: []}
  - {entity: attachment, effect: removes}
  contexts:
    agent:
      place: mcp
---

# Remove an attachment through MCP

## Trigger

An attachment is out of date.

## Outcome

It is no longer listed and its file is gone.
