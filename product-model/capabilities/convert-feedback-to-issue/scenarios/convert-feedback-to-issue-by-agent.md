---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent converts a feedback item into work to do
  kind: actor
  actor: ai-agent
  entities:
  - {entity: feedback, effect: reads, facts: [Body, Rating]}
  contexts:
    agent:
      place: mcp
- text: The Product files an issue from the feedback in its project, links the feedback to it and marks it actioned
  kind: product
  actor: ai-agent
  entities:
  - {entity: issue, effect: creates, to: Backlog, facts: [Ref, Title, Body, Author kind]}
  - {entity: feedback, effect: changes, from: New, to: Actioned, facts: [Linked issue]}
  - {entity: project, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# Turn feedback into an issue through MCP

## Trigger

A piece of feedback describes work to do.

## Outcome

The work is tracked as an issue and the feedback points to it.

## Edge cases

- Feedback already converted is refused as a conflict.
- In the web app several selected items can be converted at once.
