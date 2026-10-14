---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent lists a source's new feedback
  kind: actor
  actor: ai-agent
  entities:
  - {entity: feedback, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product returns the feedback newest first with its rating, comment, submitter and context
  kind: product
  actor: ai-agent
  entities:
  - {entity: feedback, effect: reads, facts: [Rating, Body, Submitter label, Source URL, App version, Received at, Linked issue]}
  - {entity: comment, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# Read new feedback through MCP

## Trigger

The AI agent triages what users said.

## Outcome

The AI agent sees the feedback still to be handled.
