---
appliesTo:
- type: capability
  id: claim-issue
- type: capability
  id: start-work
- type: entity
  id: project
  facts: [Agent WIP limit]
references:
- kind: code
  role: implementation
  target: apps/api/src/services/issue-leases.ts#fetchAgentWipCap
- kind: doc
  role: intent
  target: apps/docs/src/content/docs/philosophy/coordination-model.md
  title: Coordination model
- kind: doc
  role: intent
  target: apps/docs/src/content/docs/agents/workflow-spec.md
  title: Workflow spec
---

# A project never has more live agent leases than its agent WIP limit

A claim is refused once the project's issues already have as many live leases as its agent WIP limit, 3 unless the project sets another; each refusal is recorded for the factory health data. The check and the lease happen together, so two claims cannot both slip under the limit.

## Rationale

Agents make work in progress free to inflate, so the limit belongs in the claim path rather than in an operator's restraint.
