---
appliesTo:
- type: entity
  id: issue
  facts: [Parent]
references:
- kind: code
  role: implementation
  target: apps/api/src/services/issues.ts#updateIssue
---

# An issue sits at most five levels below its top ancestor, and never under itself

Setting a parent that would make an issue its own ancestor, or put it more than five levels deep, is refused.
