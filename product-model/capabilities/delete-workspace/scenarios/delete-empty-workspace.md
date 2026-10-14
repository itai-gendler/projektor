---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent asks to delete the current workspace
  kind: actor
  actor: ai-agent
  entities:
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The workspace is not the default workspace and holds no projects
  kind: condition
  actor: ai-agent
  entities:
  - {entity: workspace, effect: reads, facts: [Slug]}
  - {entity: project, effect: reads, facts: []}
  - {entity: deployment-settings, effect: reads, facts: [Default workspace]}
  contexts:
    agent:
      place: mcp
- text: The Product deletes the workspace with its memberships, groups and workspace wiki pages
  kind: product
  actor: ai-agent
  entities:
  - {entity: workspace, effect: removes}
  - {entity: workspace-membership, effect: removes, with: workspace}
  - {entity: group, effect: removes, with: workspace}
  - {entity: wiki-page, as: live-wiki-page, effect: removes, from: Live, with: workspace}
  - {entity: wiki-page, as: trashed-wiki-page, effect: removes, from: Trashed, with: workspace}
  contexts:
    agent:
      place: mcp
---

# Delete an empty workspace

## Trigger

A workspace is no longer needed.

## Outcome

The workspace and everything in it are gone for good.
