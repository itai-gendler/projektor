---
kind: alternative
routes:
  agent: MCP
steps:
- text: The AI agent claims an issue whose lease belongs to a session silent for more than 120 seconds
  kind: actor
  actor: ai-agent
  entities:
  - {entity: agent-session, effect: reads, facts: [Last heartbeat]}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product releases the old lease as expired and leases the issue to the claimer in the same call
  kind: product
  actor: ai-agent
  entities:
  - {entity: issue-lease, as: old-lease, effect: changes, from: Held, to: Released, facts: [Released at, Release reason]}
  - {entity: issue-lease, as: new-lease, effect: creates, to: Held, facts: [Claimed at]}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# Take over a lease from a quiet session

## Trigger

An agent crashed while holding an issue.

## Outcome

The issue is worked again without anyone clearing it by hand.
