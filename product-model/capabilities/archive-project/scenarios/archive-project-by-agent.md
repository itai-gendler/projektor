---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent archives the project
  kind: actor
  actor: ai-agent
  entities:
  - {entity: project, effect: reads, facts: [Name]}
  contexts:
    agent:
      place: mcp
- text: The Product marks the project archived
  kind: product
  actor: ai-agent
  entities:
  - {entity: project, effect: changes, from: Active, to: Archived, facts: [Archived at]}
  contexts:
    agent:
      place: mcp
---

# Archive a project through MCP

## Trigger

A project's work is over but should be kept.

## Outcome

The project is hidden from the default list and its share links no longer open.
