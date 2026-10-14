---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent finishes its session, moving the issue to In review with a completion report
  kind: actor
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product moves the issue to review with the report posted as a comment
  kind: product
  actor: ai-agent
  entities:
  - {entity: issue, effect: changes, from: In progress, to: In review, facts: [Completion report, In review at]}
  - {entity: comment, effect: creates, facts: [Body, Author kind, Posted at]}
  contexts:
    agent:
      place: mcp
- text: The Product ends the agent session and releases its issue lease and file claims
  kind: product
  actor: ai-agent
  entities:
  - {entity: agent-session, effect: changes, from: Active, to: Ended, facts: [Ended at]}
  - {entity: issue-lease, effect: changes, from: Held, to: Released, facts: [Released at, Release reason]}
  - {entity: file-claim, effect: changes, from: Held, to: Released, facts: [Released at, Release reason]}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# Finish work and hand it in

## Trigger

An agent completes the work it started.

## Outcome

The issue waits in review and the session holds nothing.
