---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent opens the project list
  kind: actor
  actor: ai-agent
  entities:
  - {entity: project, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product lists the active projects the actor can see
  kind: product
  actor: ai-agent
  entities:
  - {entity: project, effect: reads, facts: [Name, Key, Description]}
  contexts:
    agent:
      place: mcp
---

# Browse visible projects through MCP

## Trigger

The AI agent wants to pick a project to work in.

## Outcome

The AI agent sees exactly the projects they have access to.
