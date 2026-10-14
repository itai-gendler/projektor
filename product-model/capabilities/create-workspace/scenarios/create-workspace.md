---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent asks for a new workspace with a name and a slug
  kind: actor
  actor: ai-agent
  entities:
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product creates the workspace with its defaults and a workspace membership making the agent's person its owner
  kind: product
  actor: ai-agent
  entities:
  - {entity: workspace, effect: creates, facts: [Name, Slug]}
  - {entity: workspace-membership, effect: creates, facts: [Role, Joined at], with: workspace}
  contexts:
    agent:
      place: mcp
---

# Create a workspace

## Trigger

A person's agent needs a separate workspace.

## Outcome

The new workspace exists, owned by the agent's person.

## Edge cases

- A slug another workspace already uses is refused as a conflict.
