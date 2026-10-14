---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent asks for the workflow spec
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp
- text: The Product returns the rules the deployment ships with and their version
  kind: product
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp
---

# Fetch the workflow rules

## Trigger

An agent is about to claim work.

## Outcome

The AI agent works to the rules the deployed version enforces.
