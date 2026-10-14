---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent ends its session
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp
- text: The Product ends the agent session and releases its issue leases and file claims as agent ended
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

# End a session cleanly

## Trigger

An agent's run is over.

## Outcome

Nothing stays held by the session, and the health data shows a clean exit rather than a crash.
