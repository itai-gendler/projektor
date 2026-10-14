---
domain: projects
relations:
- entity: project-grant
  verb: receives
  cardinality: one-to-many
- entity: issue
  verb: contains
  cardinality: one-to-many
- entity: sprint
  verb: plans
  cardinality: one-to-many
- entity: wiki-page
  verb: scopes
  cardinality: one-to-many
- entity: feedback-source
  verb: gathers
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: apps/api/src/services/projects.ts#createProject
- kind: code
  role: implementation
  target: apps/api/src/services/projects.ts#updateProject
---

# Project

A body of work inside a workspace with its own issue key, issues, sprints and project wiki pages.

## Information kept

- **Name** — the project's display name
- **Key** — the uppercase prefix of its issue refs, unique within the workspace
- **Slug** — a workspace-unique short name derived from the name
- **Description** — what the project is about
- **Agent WIP limit** — how many of its issues agents may hold under live leases at once, 3 unless set
- **Close epics automatically** — whether an epic closes itself when its last open child closes
- **Archived at** — when it was archived

## States

### Active

Listed by default and open for work.

### Archived

Hidden from the default project list; its share links stop resolving.
