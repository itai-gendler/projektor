---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent opens the groups list
  kind: actor
  actor: ai-agent
  entities:
  - {entity: group, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product lists the groups the actor may see, each with its members and project grants
  kind: product
  actor: ai-agent
  entities:
  - {entity: group, effect: reads, facts: [Name, Description, Members]}
  - {entity: project-grant, effect: reads, facts: [Role]}
  - {entity: project, effect: reads, facts: [Name]}
  - {entity: workspace-membership, effect: reads, facts: [Role]}
  contexts:
    agent:
      place: mcp
---

# Browse groups through MCP

## Trigger

The AI agent wants to see who can reach which projects.

## Outcome

The AI agent sees the groups their workspace role lets them see.
