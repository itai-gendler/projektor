---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent removes a member from the workspace
  kind: actor
  actor: ai-agent
  entities:
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product deletes the member's workspace membership and remembers the removal
  kind: product
  actor: ai-agent
  entities:
  - {entity: workspace-membership, effect: removes}
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# Remove a member

## Trigger

A member should no longer reach the workspace.

## Outcome

The person is refused on their next request.
