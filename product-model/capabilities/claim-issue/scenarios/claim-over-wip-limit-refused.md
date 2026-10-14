---
kind: edge
routes:
  agent: MCP
steps:
- text: The AI agent claims a free issue in a project
  kind: actor
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: []}
  - {entity: project, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The project already has as many live leases as its agent WIP limit
  kind: condition
  actor: ai-agent
  entities:
  - {entity: project, effect: reads, facts: [Agent WIP limit]}
  - {entity: issue-lease, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product refuses the claim, naming the limit and the issues currently held, and records the refusal for the factory health data
  kind: product
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# The agent WIP limit refuses another lease

## Trigger

A fleet tries to take on more work than the project allows.

## Outcome

No lease is granted until one of the held issues is released or closed.
