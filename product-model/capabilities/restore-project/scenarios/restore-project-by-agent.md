---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent restores the archived project
  kind: actor
  actor: ai-agent
  entities:
  - {entity: project, effect: reads, facts: [Name, Archived at]}
  contexts:
    agent:
      place: mcp
- text: The Product clears the project's archived mark
  kind: product
  actor: ai-agent
  entities:
  - {entity: project, effect: changes, from: Archived, to: Active, facts: [Archived at]}
  contexts:
    agent:
      place: mcp
---

# Restore an archived project through MCP

## Trigger

Work resumes on an archived project.

## Outcome

The project is listed again.
