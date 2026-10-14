---
availability:
- place: mcp
domain: coordination
references:
- kind: code
  role: implementation
  target: apps/api/src/services/playbook-compose.ts#composePlaybook
---

# Compose playbook

An agent has a playbook filled in from live project data, such as an epic's title, its open children and the project's agent WIP limit.
