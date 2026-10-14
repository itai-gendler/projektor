---
kind: alternative
routes:
  agent: MCP
steps:
- text: The AI agent searches the wiki for words
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp
- text: The Product returns matching live pages ranked with titles above bodies, each with a highlighted snippet and its freshness
  kind: product
  actor: ai-agent
  entities:
  - {entity: wiki-page, effect: reads, facts: [Title, Slug, Freshness]}
  contexts:
    agent:
      place: mcp
---

# Search the wiki through MCP

## Trigger

The AI agent remembers what a page said but not where it is.

## Outcome

The AI agent finds matching pages from the projects they can see.
