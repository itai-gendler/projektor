---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent picks a member as the assignee
  kind: actor
  actor: ai-agent
  entities:
  - {entity: workspace-membership, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product sets the issue's assignee
  kind: product
  actor: ai-agent
  entities:
  - {entity: issue, effect: changes, facts: [Assignee]}
  contexts:
    agent:
      place: mcp
---

# Assign an issue through MCP

## Trigger

Someone should own an issue.

## Outcome

The issue shows its assignee and appears in their My Issues.

## Edge cases

- Someone who is not a member of the workspace is refused.
