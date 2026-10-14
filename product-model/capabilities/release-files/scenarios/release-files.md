---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent releases the paths it claimed
  kind: actor
  actor: ai-agent
  entities:
  - {entity: file-claim, effect: reads, facts: [Path]}
  contexts:
    agent:
      place: mcp
- text: The Product releases the file claims
  kind: product
  actor: ai-agent
  entities:
  - {entity: file-claim, effect: changes, from: Held, to: Released, facts: [Released at, Release reason]}
  contexts:
    agent:
      place: mcp
---

# Release claimed files

## Trigger

An agent is done with some files.

## Outcome

The paths are free for other agents.
