---
kind: validation
routes:
  agent: MCP
steps:
- text: The AI agent files an issue in a project its person holds only a Viewer grant on
  kind: actor
  actor: ai-agent
  entities:
  - {entity: project-grant, effect: reads, facts: [Role]}
  - {entity: project, effect: reads, facts: []}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
- text: The Product refuses the issue as forbidden
  kind: product
  actor: ai-agent
  entities:
  - {entity: project, effect: reads, facts: []}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# Filing into a read-only project is refused

## Trigger

An agent acting for a read-only member tries to file an issue.

## Outcome

No issue is created.

## Edge cases

- A project the person cannot see at all answers as not found instead.
