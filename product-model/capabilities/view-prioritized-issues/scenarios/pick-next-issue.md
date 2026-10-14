---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent asks for the prioritized issues, leaving out claimed ones
  kind: actor
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product ranks the visible open ready issues and leaves out those under a live lease
  kind: product
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: [Ref, Title, Priority, Story points, Definition of ready]}
  - {entity: issue-link, effect: reads, facts: [Type]}
  - {entity: issue-lease, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# Pick the next issue to work on

## Trigger

An agent is free for work.

## Outcome

The AI agent has a ranked list of issues nobody holds.
