---
domain: issues
relations:
- entity: link-visitor
  verb: admits
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: apps/api/src/services/share.ts#createShareToken
---

# Share link

A public link that shows one issue, read-only, to anyone who holds it.

## Information kept

- **Expires at** — three days after it was created
