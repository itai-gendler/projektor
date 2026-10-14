---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent registers a session with a name and the issue it will work
  kind: actor
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product creates a live agent session linked to the issue and returns its id
  kind: product
  actor: ai-agent
  entities:
  - {entity: agent-session, effect: creates, to: Active, facts: [Name, Linked issue, Credential, Started at, Last heartbeat]}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
references:
- kind: code
  role: implementation
  target: apps/api/src/services/agent-identity.ts
---

# Register a session

## Trigger

An agent starts a run in the workspace.

## Outcome

The AI agent has a live session to lease issues and claim files with.

## Edge cases

- With exactly one live session on its credential an agent may later omit the session id; with several, or none, an omitted id is refused as ambiguous.
