---
appliesTo:
- type: capability
  id: change-issue-status
- type: capability
  id: finish-work
- type: entity
  id: issue
  effect: changes
  to: In review
references:
- kind: code
  role: implementation
  target: apps/api/src/services/issues.ts#updateIssue
- kind: doc
  role: intent
  target: apps/docs/src/content/docs/agents/workflow-spec.md
  title: Workflow spec
---

# An issue a live agent holds enters review only with a completion report

Moving an issue into a review-step status while a live agent session leases it needs a completion report with a summary and a verification; the report is kept on the issue and posted as a comment.
