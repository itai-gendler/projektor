---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent writes a comment on an issue
  kind: actor
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: [Title]}
  - {entity: comment, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product adds the comment, marked as written by a person or an agent according to how the actor signed in
  kind: product
  actor: ai-agent
  entities:
  - {entity: comment, effect: creates, facts: [Body, Author kind, Posted at]}
  contexts:
    agent:
      place: mcp
---

# Comment on an issue through MCP

## Trigger

The AI agent has something to say about an issue.

## Outcome

The comment is on the issue's timeline.
