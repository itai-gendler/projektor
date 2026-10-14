---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent attaches a page of the wiki by its title
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp
- text: The Product attaches a reference to the page
  kind: product
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: []}
  - {entity: attachment, effect: creates, facts: [Kind, Attached at]}
  contexts:
    agent:
      place: mcp
---

# Attach a wiki page to an issue through MCP

## Trigger

An issue's background lives in the wiki.

## Outcome

The issue links to the page, which still resolves after a rename.
