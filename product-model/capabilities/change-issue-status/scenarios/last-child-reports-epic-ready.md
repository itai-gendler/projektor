---
kind: alternative
routes:
  agent: MCP
steps:
- text: The AI agent closes the last open child of an epic
  kind: actor
  actor: ai-agent
  entities:
  - {entity: issue, as: child, effect: reads, facts: [Parent]}
  contexts:
    agent:
      place: mcp
- text: The Product closes the child
  kind: product
  actor: ai-agent
  entities:
  - {entity: issue, as: child, effect: changes, from: In progress, to: Done, facts: [Done at]}
  contexts:
    agent:
      place: mcp
- text: The epic's project does not close epics automatically
  kind: condition
  actor: ai-agent
  entities:
  - {entity: project, effect: reads, facts: [Close epics automatically]}
  contexts:
    agent:
      place: mcp
- text: The Product answers that the epic is ready to close, naming its ref
  kind: product
  actor: ai-agent
  entities:
  - {entity: issue, as: epic, effect: reads, facts: [Ref]}
  contexts:
    agent:
      place: mcp
---

# Closing an epic's last open child reports the epic ready to close

## Trigger

The last piece of an epic is finished in a project that leaves closing epics to people.

## Outcome

The epic stays open and the agent knows it can be closed.
