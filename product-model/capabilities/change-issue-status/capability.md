---
availability:
- place: web::workspace
- place: mcp
domain: issues
references:
- kind: code
  role: implementation
  target: apps/api/src/services/issues.ts#updateIssue
- kind: doc
  role: intent
  target: apps/docs/src/content/docs/agents/workflow-spec.md
  title: Workflow spec
---

# Change issue status

A member with write access moves an issue to another of the workspace's statuses: from the board, the issue page, or an agent's update. Any status may follow any other; what each move means depends on the status's category, and moves into review or done carry the completion report rules.
