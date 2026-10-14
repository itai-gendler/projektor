---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent moves the issue it holds to In review with a completion report naming what changed, how it was verified and the pull request
  kind: actor
  actor: ai-agent
  entities:
  - {entity: issue-lease, effect: reads, facts: []}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product moves the issue to review, keeps the report, posts it as a comment and stamps when review began
  kind: product
  actor: ai-agent
  entities:
  - {entity: issue, effect: changes, from: In progress, to: In review, facts: [Completion report, In review at]}
  - {entity: comment, effect: creates, facts: [Body, Author kind, Posted at]}
  contexts:
    agent:
      place: mcp
---

# An agent hands work in with a completion report

## Trigger

An agent finishes implementing an issue it leased.

## Outcome

The issue waits in review with its completion report on the timeline.
