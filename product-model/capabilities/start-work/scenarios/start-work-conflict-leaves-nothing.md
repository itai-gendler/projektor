---
kind: edge
routes:
  agent: MCP
steps:
- text: The AI agent starts work on an issue another live agent holds
  kind: actor
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product registers a session for the attempt
  kind: product
  actor: ai-agent
  entities:
  - {entity: agent-session, effect: creates, to: Active, facts: [Name, Linked issue, Credential, Started at, Last heartbeat]}
  contexts:
    agent:
      place: mcp
- text: The issue is already leased by a live session, a requested path is held, or the project is at its agent WIP limit
  kind: condition
  actor: ai-agent
  entities:
  - {entity: issue-lease, effect: reads, facts: []}
  - {entity: file-claim, effect: reads, facts: [Path]}
  - {entity: project, effect: reads, facts: []}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product ends the new session and answers with the same conflict a separate claim would give
  kind: product
  actor: ai-agent
  entities:
  - {entity: agent-session, effect: changes, from: Active, to: Ended, facts: [Ended at]}
  contexts:
    agent:
      place: mcp
---

# A conflict while starting leaves nothing claimed

## Trigger

Two agents reach for the same issue.

## Outcome

Nothing is held by the failed attempt.

## Edge cases

- If the agent's process dies mid-call, what it claimed becomes reclaimable once its session has been quiet for 120 seconds.
