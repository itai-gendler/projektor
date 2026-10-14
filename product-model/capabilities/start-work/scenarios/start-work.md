---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent starts work on an issue with a name and the paths it will edit
  kind: actor
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product registers a live agent session
  kind: product
  actor: ai-agent
  entities:
  - {entity: agent-session, effect: creates, to: Active, facts: [Name, Linked issue, Credential, Started at, Last heartbeat]}
  contexts:
    agent:
      place: mcp
- text: The Product leases the issue to the session, within the project's agent WIP limit
  kind: product
  actor: ai-agent
  entities:
  - {entity: issue-lease, effect: creates, to: Held, facts: [Claimed at]}
  - {entity: project, effect: reads, facts: [Agent WIP limit]}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product claims the paths for the issue
  kind: product
  actor: ai-agent
  entities:
  - {entity: file-claim, effect: creates, to: Held, facts: [Path, Claimed at]}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product posts a started message to the issue's channel
  kind: product
  actor: ai-agent
  entities:
  - {entity: coordination-message, effect: creates, facts: [Channel, Body, Posted at]}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# Start work on an issue

## Trigger

An agent picks up an issue.

## Outcome

The AI agent holds the issue and its files and has a session id to finish with.
