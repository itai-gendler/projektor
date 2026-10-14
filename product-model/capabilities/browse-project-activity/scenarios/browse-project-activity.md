---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent asks for a project's activity since a moment
  kind: actor
  actor: ai-agent
  entities:
  - {entity: project, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product merges the project's recent issue, comment, status, wiki page and sprint events, newest first
  kind: product
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: [Ref, Title]}
  - {entity: comment, effect: reads, facts: [Posted at]}
  - {entity: wiki-page, effect: reads, facts: [Title]}
  - {entity: sprint, effect: reads, facts: [Name]}
  - {entity: project, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# Catch up on a project

## Trigger

An agent joins a project mid-stream.

## Outcome

The AI agent knows what happened recently.
