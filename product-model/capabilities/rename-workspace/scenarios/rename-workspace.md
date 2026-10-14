---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent gives the current workspace a new name
  kind: actor
  actor: ai-agent
  entities:
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product saves the workspace's new name
  kind: product
  actor: ai-agent
  entities:
  - {entity: workspace, effect: changes, facts: [Name]}
  contexts:
    agent:
      place: mcp
---

# Rename the workspace

## Trigger

The workspace's name no longer fits.

## Outcome

The workspace carries the new name.
