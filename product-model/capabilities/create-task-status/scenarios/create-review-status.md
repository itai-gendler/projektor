---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent adds a Code review status in the In progress category marked as a review step
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp
- text: The Product adds the task status; issues entering it from now on are handed in for review
  kind: product
  actor: ai-agent
  entities:
  - {entity: task-status, effect: creates, facts: [Key, Name, Category, Position, Default, Review step, Backlog]}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# Add a review step

## Trigger

A team wants its own review stage.

## Outcome

The new status is offered for issues and carries the review rules.

## Edge cases

- A key the workspace already uses is refused.
- Making the new status the default takes the default from the previous one.
