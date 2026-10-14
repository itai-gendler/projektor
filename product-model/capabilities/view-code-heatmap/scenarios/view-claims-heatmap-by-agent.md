---
kind: alternative
routes:
  agent: MCP
steps:
- text: The AI agent opens the code heatmap
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp
- text: The Product groups file claims one folder level below the chosen prefix, sized by how many distinct issues claimed there
  kind: product
  actor: ai-agent
  entities:
  - {entity: file-claim, effect: reads, facts: [Path, Claimed at]}
  - {entity: group, effect: reads, facts: []}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# See where work lands through MCP

## Trigger

The AI agent wants to see which parts of the code get the most work.

## Outcome

The AI agent sees the busiest folders.
