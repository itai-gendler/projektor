---
kind: alternative
routes:
  agent: MCP
steps:
- text: The AI agent claims a path held by a claim made without any agent session
  kind: actor
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: []}
  - {entity: agent-session, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The agentless claim is older than the deployment's agentless claim expiry
  kind: condition
  actor: ai-agent
  entities:
  - {entity: deployment-settings, effect: reads, facts: [Agentless claim expiry]}
  - {entity: file-claim, as: agentless, effect: reads, facts: [Claimed at]}
  contexts:
    agent:
      place: mcp
- text: The Product releases the agentless claim as expired and claims the path
  kind: product
  actor: ai-agent
  entities:
  - {entity: file-claim, as: agentless, effect: changes, from: Held, to: Released, facts: [Released at, Release reason]}
  - {entity: file-claim, as: replacement, effect: creates, to: Held, facts: [Path, Claimed at]}
  contexts:
    agent:
      place: mcp
---

# An agentless claim expires

## Trigger

A claim was made without a session and forgotten.

## Outcome

After the expiry, 24 hours unless the operator set otherwise, the path can be claimed.
