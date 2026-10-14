---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent lists file claims for a path before deciding whether to claim it
  kind: actor
  actor: ai-agent
  entities:
  - {entity: file-claim, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product returns the held claims that are still live, each with its issue and session
  kind: product
  actor: ai-agent
  entities:
  - {entity: file-claim, effect: reads, facts: [Path, Claimed at]}
  - {entity: issue, effect: reads, facts: [Ref]}
  - {entity: agent-session, effect: reads, facts: [Name]}
  contexts:
    agent:
      place: mcp
---

# See which files are taken

## Trigger

An agent wants to avoid a conflict.

## Outcome

The AI agent knows whether the path is free.
