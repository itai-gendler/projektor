---
kind: alternative
routes:
  agent: MCP
steps:
- text: The AI agent files an issue whose body states acceptance criteria and the files in scope, straight into To do
  kind: actor
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product creates the issue in To do, records it as meeting the definition of ready, marks it as written by an agent and stamps when it became ready
  kind: product
  actor: ai-agent
  entities:
  - {entity: project, effect: reads, facts: [Key]}
  - {entity: issue, effect: creates, to: To do, facts: [Ref, Title, Body, Definition of ready, Author kind, Ready at]}
  contexts:
    agent:
      place: mcp
---

# An agent files an issue ready for pickup

## Trigger

An agent breaks work down into tickets other agents can pick up.

## Outcome

The issue is ready and can be offered to agents looking for work.
