---
appliesTo:
- type: entity
  id: issue
  facts: [Ref]
references:
- kind: code
  role: implementation
  target: apps/api/src/services/issues.ts#createIssue
---

# Each issue gets the next number in its project

An issue's ref is its project's key and a number one higher than any issue the project has had, never reused within the project.
