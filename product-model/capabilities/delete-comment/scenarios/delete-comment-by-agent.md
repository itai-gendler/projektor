---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent deletes a comment
  kind: actor
  actor: ai-agent
  entities:
  - {entity: comment, effect: reads, facts: [Body]}
  contexts:
    agent:
      place: mcp
- text: The Product removes the comment
  kind: product
  actor: ai-agent
  entities:
  - {entity: comment, effect: removes}
  contexts:
    agent:
      place: mcp
---

# Delete a comment through MCP

## Trigger

A comment should not stay on the issue.

## Outcome

The comment is gone.
