---
kind: validation
routes:
  agent: MCP
steps:
- text: The AI agent asks for an issue whose project none of its person's groups is granted
  kind: actor
  actor: ai-agent
  entities:
  - {entity: project, effect: reads, facts: []}
  - {entity: group, effect: reads, facts: []}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product answers that the issue was not found, exactly as for an issue that does not exist
  kind: product
  actor: ai-agent
  entities:
  - {entity: project, effect: reads, facts: []}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# An issue in an ungranted project looks missing

## Trigger

An agent guesses or is handed a ref in a project its person cannot see.

## Outcome

The issue's existence is not revealed.
