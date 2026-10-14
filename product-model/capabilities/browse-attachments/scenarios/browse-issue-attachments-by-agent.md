---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent looks at an issue's attachments
  kind: actor
  actor: ai-agent
  entities:
  - {entity: attachment, effect: reads, facts: []}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product lists them with their kind, name and size
  kind: product
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: []}
  - {entity: attachment, effect: reads, facts: [Kind, File name, Size, URL, Attached at]}
  contexts:
    agent:
      place: mcp
---

# List an issue's attachments through MCP

## Trigger

The AI agent needs the material attached to an issue.

## Outcome

The AI agent sees every attachment; an agent gets file metadata, the bytes come from the web app.
