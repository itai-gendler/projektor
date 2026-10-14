---
appliesTo:
- type: entity
  id: issue
  facts: [Needs audit]
references:
- kind: code
  role: implementation
  target: apps/api/src/services/evidence-classification.ts
- kind: doc
  role: intent
  target: apps/docs/src/content/docs/agents/workflow-spec.md
  title: Workflow spec
---

# An agent's done closure with nothing checkable is flagged for audit

When an agent closes an issue as done and its verification has no pull request, CI run, commit link or commit hash, the issue is flagged as needing audit. The flag never blocks the close.
