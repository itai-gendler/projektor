---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent sets the workspace's display name and accent color, clearing the font back to the default
  kind: actor
  actor: ai-agent
  entities:
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product saves the workspace's branding
  kind: product
  actor: ai-agent
  entities:
  - {entity: workspace, effect: changes, facts: [Branding]}
  contexts:
    agent:
      place: mcp
---

# Brand the workspace

## Trigger

A team wants the workspace to look like its own.

## Outcome

The workspace and its share links show the branding.
