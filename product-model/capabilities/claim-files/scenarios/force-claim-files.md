---
kind: alternative
routes:
  agent: MCP
steps:
- text: The AI agent claims a held path with force
  kind: actor
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: Every holder's issue is visible to the claimer
  kind: condition
  actor: ai-agent
  entities:
  - {entity: file-claim, as: held, effect: reads, facts: [Path]}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product releases the holder's claim as overridden, claims the path, and posts a message to both issues' channels
  kind: product
  actor: ai-agent
  entities:
  - {entity: file-claim, as: held, effect: changes, from: Held, to: Released, facts: [Released at, Release reason]}
  - {entity: file-claim, as: new-claim, effect: creates, to: Held, facts: [Path, Claimed at]}
  - {entity: coordination-message, effect: creates, facts: [Channel, Body, Posted at]}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# Force a claim over a live holder

## Trigger

An agent must edit a file another agent holds and decides to take it.

## Outcome

The path is the claimer's and the displaced agent is told.

## Edge cases

- Force cannot override a holder whose issue the claimer cannot see; the claim is refused instead.
