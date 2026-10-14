---
availability:
- place: mcp
domain: issues
references:
- kind: code
  role: implementation
  target: apps/api/src/services/issues.ts#getPrioritizedIssues
- kind: doc
  role: intent
  target: apps/docs/src/content/docs/agents/workflow-spec.md
  title: Definition of ready
---

# View prioritized issues

An agent asks what to work on next and gets open issues ranked by how many others they block, their priority and how small they are. Issues that miss the definition of ready, sit in the backlog, or are held by a live lease are left out unless asked for.
