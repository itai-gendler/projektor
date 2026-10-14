---
kind: alternative
routes:
  agent: MCP
steps:
- text: The AI agent replaces one section of a page, addressed by its heading
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp
- text: The Product keeps the previous content as a page revision and saves the patched page
  kind: product
  actor: ai-agent
  entities:
  - {entity: wiki-revision, effect: creates, facts: [Content, Title, Author, Saved at]}
  - {entity: wiki-page, effect: changes, facts: [Content]}
  contexts:
    agent:
      place: mcp
---

# An agent patches one section

## Trigger

An agent changes one part of a long page.

## Outcome

Only that section changed; the agent never rewrote the whole page.
