---
kind: validation
routes:
  agent: MCP
steps:
- text: The AI agent sets an issue to Done without a completion report
  kind: actor
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: An agent leased the issue at some point and no completion report is on file
  kind: condition
  actor: ai-agent
  entities:
  - {entity: issue-lease, effect: reads, facts: []}
  - {entity: issue, effect: reads, facts: [Completion report]}
  contexts:
    agent:
      place: mcp
- text: The Product refuses the close until a completion report is supplied
  kind: product
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp
---

# An agent-worked issue cannot close without a report

## Trigger

Someone tries to close an issue an agent worked on without saying what was done.

## Outcome

The issue stays open until a close carries a completion report.

## Edge cases

- Cancelling the same issue is not blocked.
