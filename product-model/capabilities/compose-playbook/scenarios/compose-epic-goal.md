---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent composes the epic-goal playbook for an epic by its ref
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp
- text: The Product fills the playbook with the epic's title, its open children and the project's agent WIP limit
  kind: product
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: [Ref, Title, Child rollup]}
  - {entity: project, effect: reads, facts: [Agent WIP limit]}
  contexts:
    agent:
      place: mcp
---

# Compose the epic-goal playbook

## Trigger

An agent takes on a whole epic.

## Outcome

The AI agent has a directive written for that epic.

## Edge cases

- A playbook that cannot be composed is answered as not found.
