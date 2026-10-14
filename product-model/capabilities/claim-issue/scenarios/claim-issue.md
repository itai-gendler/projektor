---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent claims an issue for its live session
  kind: actor
  actor: ai-agent
  entities:
  - {entity: agent-session, effect: reads, facts: [Last heartbeat]}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: No live session holds the issue and the project has fewer live leases than its agent WIP limit
  kind: condition
  actor: ai-agent
  entities:
  - {entity: project, effect: reads, facts: [Agent WIP limit]}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product leases the issue to the agent session and refreshes its heartbeat
  kind: product
  actor: ai-agent
  entities:
  - {entity: issue-lease, effect: creates, to: Held, facts: [Claimed at]}
  - {entity: agent-session, effect: changes, facts: [Last heartbeat]}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# Lease a free issue

## Trigger

An agent picks the next issue to work.

## Outcome

The issue is the agent's alone until it is released, closed or the session goes quiet.

## Edge cases

- Leasing an issue does not change its status.
