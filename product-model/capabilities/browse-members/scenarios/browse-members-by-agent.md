---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent lists the members
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp
- text: The Product returns each member's name, email and workspace role
  kind: product
  actor: ai-agent
  entities:
  - {entity: user, effect: reads, facts: [Email, Name]}
  - {entity: workspace-membership, effect: reads, facts: [Role]}
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# List the workspace's members through MCP

## Trigger

The AI agent wants to know who is in the workspace.

## Outcome

The AI agent sees every member and their role.
