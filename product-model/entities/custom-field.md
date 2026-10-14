---
domain: custom-fields
references:
- kind: code
  role: implementation
  target: apps/api/src/services/custom-fields.ts#createCustomFieldDef
- kind: code
  role: implementation
  target: apps/api/src/services/custom-fields.ts#seedDefaultCustomFields
---

# Custom field definition

An extra field the workspace keeps on issues, for every project or for one. A new workspace has a story points field.

## Information kept

- **Key** — the stable machine name, unique in the workspace
- **Label** — the label people see
- **Field type** — text, number, select, date or user
- **Options** — the choices of a select field
- **Project** — the one project it applies to, if any
- **Internal** — whether it is kept off share links
