---
kind: alternative
routes:
  agent: MCP
steps:
- text: The AI agent claims paths held by a session silent for more than 120 seconds
  kind: actor
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: []}
  - {entity: agent-session, effect: reads, facts: [Last heartbeat]}
  contexts:
    agent:
      place: mcp
- text: The Product releases the old claims as expired without recording a conflict and claims the paths
  kind: product
  actor: ai-agent
  entities:
  - {entity: file-claim, as: stale, effect: changes, from: Held, to: Released, facts: [Released at, Release reason]}
  - {entity: file-claim, as: fresh, effect: creates, to: Held, facts: [Path, Claimed at]}
  contexts:
    agent:
      place: mcp
---

# Take over files from a quiet session

## Trigger

An agent died while holding files.

## Outcome

The files are claimable again without anyone clearing them.
