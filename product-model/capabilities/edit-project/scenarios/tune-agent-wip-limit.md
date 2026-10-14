---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent sets a new agent WIP limit and whether epics close automatically
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp
- text: The Product saves the project's settings; later issue leases are admitted against the new limit
  kind: product
  actor: ai-agent
  entities:
  - {entity: project, effect: changes, facts: [Agent WIP limit, Close epics automatically]}
  - {entity: issue-lease, effect: reads, facts: []}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# Tune a project's agent WIP limit

## Trigger

Flow metrics show the agent WIP limit is too tight or too loose.

## Outcome

New leases in the project are capped at the new limit.

## Edge cases

- Changing the key to one another project uses is refused as a conflict.
