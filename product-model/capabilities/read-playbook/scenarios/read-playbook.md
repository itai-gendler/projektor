---
kind: primary
routes:
  agent: MCP
steps:
- text: The AI agent lists the playbooks and opens the epic-goal playbook
  kind: actor
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp
- text: The Product returns the playbook as shipped with the deployment
  kind: product
  actor: ai-agent
  entities: []
  contexts:
    agent:
      place: mcp
---

# Read a playbook

## Trigger

An agent is about to work a kind of task it has a pattern for.

## Outcome

The AI agent follows the shipped pattern.
