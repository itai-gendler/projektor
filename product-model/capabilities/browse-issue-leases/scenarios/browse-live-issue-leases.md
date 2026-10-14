---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent lists issue leases
  kind: actor
  actor: ai-agent
  entities:
  - {entity: issue-lease, effect: reads, facts: []}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product returns the held leases whose session is live, each with the issue's ref and the session's name
  kind: product
  actor: ai-agent
  entities:
  - {entity: issue-lease, effect: reads, facts: [Claimed at]}
  - {entity: issue, effect: reads, facts: [Ref]}
  - {entity: agent-session, effect: reads, facts: [Name]}
  contexts:
    agent:
      place: mcp
---

# See which issues are taken

## Trigger

An agent checks what the fleet is working on.

## Outcome

The AI agent sees who holds which issue.

## Edge cases

- Asking to include stale leases also returns held leases whose session went quiet, marked as not live.
