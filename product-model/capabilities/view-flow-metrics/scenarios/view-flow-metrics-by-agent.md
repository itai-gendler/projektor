---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent opens the metrics for a time window
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp
- text: The Product computes the project's flow from the times its issues first became ready, started, entered review and were done, and from how its leases ended
  kind: product
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: [Ready at, Started at, In review at, Done at, Review bounces]}
  - {entity: issue-lease, effect: reads, facts: [Release reason]}
  - {entity: project, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# Read a project's flow through MCP

## Trigger

The AI agent wants to know whether the agent WIP limit is about right.

## Outcome

The AI agent sees how work flows through the project.

## Edge cases

- Cycle time starts when an issue first enters an in-progress or review status, not when an agent leases it.
