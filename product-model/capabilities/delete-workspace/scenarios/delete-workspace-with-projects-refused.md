---
kind: validation
routes:
  agent: MCP
steps:
- text: The AI agent asks to delete a workspace that still contains a project
  kind: actor
  actor: ai-agent
  entities:
  - {entity: workspace, effect: reads, facts: []}
  - {entity: project, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The workspace still contains a project
  kind: condition
  actor: ai-agent
  entities:
  - {entity: workspace, effect: reads, facts: [Name]}
  - {entity: project, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product refuses the deletion as a conflict and keeps the workspace
  kind: product
  actor: ai-agent
  entities:
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# Deleting a workspace that still has projects is refused

## Trigger

Someone tries to delete a workspace before deleting its projects.

## Outcome

Nothing is deleted; every project must be deleted first.

## Edge cases

- Deleting the default workspace is refused whatever it holds.
