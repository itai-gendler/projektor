---
domain: groups
relations:
- entity: user
  verb: includes
  cardinality: many-to-many
- entity: project-grant
  verb: carries
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: apps/api/src/services/groups.ts#createGroup
- kind: doc
  role: intent
  target: apps/docs/src/content/docs/architecture/access-control.mdx
  title: Access control
---

# Group

An access group in a workspace: a set of members and the projects granted to it. Group grants are how an ordinary member comes to see a project at all.

## Information kept

- **Name** — unique within the workspace
- **Description** — what the group is for
- **Members** — the workspace members it includes
