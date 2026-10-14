---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent deletes a page
  kind: actor
  actor: ai-agent
  entities:
  - {entity: wiki-page, as: page, effect: reads, facts: [Title]}
  contexts:
    agent:
      place: mcp
- text: The Product moves the page to the trash and moves its children up to its parent
  kind: product
  actor: ai-agent
  entities:
  - {entity: wiki-page, as: page, effect: changes, from: Live, to: Trashed, facts: [Trashed at]}
  - {entity: wiki-page, as: child, effect: changes, facts: [Parent page]}
  contexts:
    agent:
      place: mcp
---

# Move a page to the trash through MCP

## Trigger

A page is obsolete.

## Outcome

The page is out of the tree and search, restorable for 30 days.

## Edge cases

- Asking for the whole subtree trashes the children too, as one batch restored together.
