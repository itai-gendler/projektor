---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent opens an issue by its ref
  kind: actor
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product shows the issue's fields, its definition of ready, its children by state and its links
  kind: product
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: [Ref, Title, Body, Type, Priority, Labels, Assignee, Parent, Sprint, Story points, Custom fields, Child rollup, Definition of ready, Needs audit]}
  - {entity: issue-link, effect: reads, facts: [Type]}
  contexts:
    agent:
      place: mcp
---

# Open an issue through MCP

## Trigger

The AI agent needs the full picture of one issue.

## Outcome

The AI agent sees the issue as Projektor keeps it.
