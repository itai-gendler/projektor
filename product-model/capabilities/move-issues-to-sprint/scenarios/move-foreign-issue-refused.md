---
kind: validation
routes:
  agent: MCP
steps:
- text: The AI agent moves issues into a sprint, one of them from another project
  kind: actor
  actor: ai-agent
  entities:
  - {entity: sprint, effect: reads, facts: []}
  - {entity: project, effect: reads, facts: []}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product refuses the whole move, naming the issue it could not find in the sprint's project
  kind: product
  actor: ai-agent
  entities:
  - {entity: issue, effect: reads, facts: [Ref]}
  - {entity: project, effect: reads, facts: []}
  - {entity: sprint, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# An issue from another project is refused

## Trigger

An agent mixes projects when planning.

## Outcome

No issue is moved.
