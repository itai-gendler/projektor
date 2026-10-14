---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent edits a page without publishing
  kind: actor
  actor: ai-agent
  entities:
  - {entity: wiki-page, effect: reads, facts: [Content]}
  contexts:
    agent:
      place: mcp
- text: The Product keeps the edit as the actor's page draft, replacing any earlier draft of theirs for the page
  kind: product
  actor: ai-agent
  entities:
  - {entity: wiki-draft, effect: creates, facts: [Title, Content, Base revision, Saved at]}
  contexts:
    agent:
      place: mcp
---

# Keep an unsaved edit through MCP

## Trigger

The AI agent is part-way through an edit.

## Outcome

The draft can be picked up later, from any device; nobody else sees it.
