---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent purges the workspace's wiki trash
  kind: actor
  actor: ai-agent
  entities:
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product removes every page trashed for at least 30 days with its revisions and attachments
  kind: product
  actor: ai-agent
  entities:
  - {entity: wiki-page, effect: removes, from: Trashed}
  - {entity: wiki-revision, effect: removes, with: wiki-page}
  - {entity: attachment, effect: removes, with: wiki-page}
  contexts:
    agent:
      place: mcp
---

# Purge expired trash

## Trigger

An admin clears out the trash.

## Outcome

Expired pages are gone for good; younger ones stay restorable.
