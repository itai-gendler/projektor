---
kind: validation
routes:
  agent: MCP
steps:
- text: The AI agent asks to remove its own person from the workspace
  kind: actor
  actor: ai-agent
  entities:
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product refuses the removal and keeps the workspace membership
  kind: product
  actor: ai-agent
  entities:
  - {entity: workspace-membership, effect: reads, facts: [Role]}
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# An owner cannot remove themselves

## Trigger

An owner tries to remove their own membership.

## Outcome

The owner stays a member.
