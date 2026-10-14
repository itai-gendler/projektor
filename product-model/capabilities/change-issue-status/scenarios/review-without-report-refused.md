---
kind: validation
routes:
  agent: MCP
steps:
- text: The AI agent moves an issue to In review without a completion report
  kind: actor
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: A live agent session holds a lease on the issue
  kind: condition
  actor: ai-agent
  entities:
  - {entity: issue-lease, effect: reads, facts: []}
  - {entity: agent-session, effect: reads, facts: [Last heartbeat]}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product refuses the move, naming the missing summary and verification
  kind: product
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: [Completion report]}
  contexts:
    agent:
      place: mcp
---

# Entering review without a report is refused while an agent holds the issue

## Trigger

An agent tries to hand work in without saying what it did.

## Outcome

The issue stays where it was.
