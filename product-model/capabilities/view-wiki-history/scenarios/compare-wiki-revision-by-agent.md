---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent opens the page's history and picks a revision
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp
- text: The Product lists the revisions and shows the difference between the chosen one and the current content
  kind: product
  actor: ai-agent
  entities:
  - {entity: wiki-revision, effect: reads, facts: [Title, Summary, Author, Saved at, Content]}
  - {entity: wiki-page, effect: reads, facts: [Content]}
  contexts:
    agent:
      place: mcp
---

# Compare a revision with the current page through MCP

## Trigger

The AI agent wants to know what changed on a page.

## Outcome

The AI agent sees who changed what and when.
