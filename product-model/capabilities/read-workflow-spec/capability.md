---
availability:
- place: mcp
domain: coordination
references:
- kind: code
  role: implementation
  target: apps/api/src/services/workflow.ts#getWorkflow
- kind: doc
  role: intent
  target: apps/docs/src/content/docs/agents/workflow-spec.md
  title: Workflow spec
---

# Read workflow spec

An agent fetches the canonical workflow rules, the definition of ready, the states, the human gates, completion reports and WIP limits, with a content version, before claiming work.
