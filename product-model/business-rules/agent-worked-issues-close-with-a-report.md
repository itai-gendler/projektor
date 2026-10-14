---
appliesTo:
- type: capability
  id: change-issue-status
- type: entity
  id: issue
  effect: changes
  to: Done
references:
- kind: code
  role: implementation
  target: apps/api/src/services/issues.ts#updateIssue
- kind: doc
  role: intent
  target: apps/docs/src/content/docs/agents/workflow-spec.md
  title: Workflow spec
---

# An issue any agent ever leased closes as done only with a completion report

Moving an issue that any agent session has ever leased to a done status needs a completion report, either carried by that update or already on file. Cancelling is not gated, and issues no agent leased close freely.

## Rationale

Agents close their own work without a human gate, so the evidence of what was done must travel with every agent-worked close.
