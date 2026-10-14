---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent claims a list of exact paths for its issue and session
  kind: actor
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: No live claim holds any of the paths
  kind: condition
  actor: ai-agent
  entities:
  - {entity: file-claim, effect: reads, facts: [Path]}
  contexts:
    agent:
      place: mcp
- text: The Product claims every path and refreshes the session's heartbeat
  kind: product
  actor: ai-agent
  entities:
  - {entity: file-claim, effect: creates, to: Held, facts: [Path, Claimed at]}
  - {entity: agent-session, effect: changes, facts: [Last heartbeat]}
  contexts:
    agent:
      place: mcp
---

# Claim the files to edit

## Trigger

An agent is about to edit files.

## Outcome

The fleet can see the paths are taken.

## Edge cases

- A path listed twice is claimed once.
- At most 100 paths go in one claim.
