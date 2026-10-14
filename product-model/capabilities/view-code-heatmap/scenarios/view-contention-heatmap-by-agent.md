---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent switches the code heatmap to contention
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp
- text: The Product groups the claim conflicts one folder level below the chosen prefix and ranks them
  kind: product
  actor: ai-agent
  entities:
  - {entity: claim-conflict, effect: reads, facts: [Path, Forced, Occurred at]}
  - {entity: group, effect: reads, facts: []}
  contexts:
    agent:
      place: mcp
---

# See where agents collide through MCP

## Trigger

The AI agent wonders how the work is being sliced.

## Outcome

The AI agent sees which folders agents keep colliding on.
