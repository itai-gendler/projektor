---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent gives the new project a name, a key and optionally a description
  kind: actor
  actor: ai-agent
  entities:
  - {entity: project, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product creates the project with a slug derived from its name
  kind: product
  actor: ai-agent
  entities:
  - {entity: project, effect: creates, to: Active, facts: [Name, Key, Slug, Description, Agent WIP limit]}
  contexts:
    agent:
      place: mcp
---

# Create a project through MCP

## Trigger

The AI agent starts a new body of work.

## Outcome

The project exists; only owners and admins see it until it is granted to a group.

## Edge cases

- A key another project in the workspace already uses is refused as a conflict.
