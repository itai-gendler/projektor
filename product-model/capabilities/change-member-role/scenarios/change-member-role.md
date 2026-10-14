---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent sets a member's role to Owner, Admin, Member or Viewer
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp
- text: The Product saves the new role on the workspace membership, effective on the member's next request
  kind: product
  actor: ai-agent
  entities:
  - {entity: workspace-membership, effect: changes, facts: [Role]}
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# Change a member's role

## Trigger

A member's responsibilities change.

## Outcome

The member holds the new role.
