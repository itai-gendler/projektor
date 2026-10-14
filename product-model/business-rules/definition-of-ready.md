---
appliesTo:
- type: entity
  id: issue
  facts: [Definition of ready]
- type: capability
  id: view-prioritized-issues
references:
- kind: code
  role: implementation
  target: apps/api/src/services/definition-of-ready.ts#checkDefinitionOfReady
- kind: doc
  role: intent
  target: apps/docs/src/content/docs/agents/workflow-spec.md
  title: Workflow spec
---

# An issue is ready for an agent when its body states acceptance criteria and a scope of files

The definition of ready is checked whenever an issue's body is written: it needs an acceptance criteria section with content and either a scope or files section or a file path in code formatting. Issues that miss it are left out of the prioritized issues unless asked for.
