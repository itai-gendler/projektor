---
domain: workspace
relations:
- entity: workspace-membership
  verb: admits
  cardinality: one-to-many
- entity: project
  verb: contains
  cardinality: one-to-many
- entity: group
  verb: defines
  cardinality: one-to-many
- entity: task-status
  verb: configures
  cardinality: one-to-many
- entity: wiki-page
  verb: keeps
  cardinality: one-to-many
- entity: api-token
  verb: issues
  cardinality: one-to-many
- entity: agent-session
  verb: hosts
  cardinality: one-to-many
- entity: coordination-message
  verb: carries
  cardinality: one-to-many
- entity: task-type
  verb: offers
  cardinality: one-to-many
- entity: custom-field
  verb: defines
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: apps/api/src/services/workspaces.ts#createWorkspace
- kind: code
  role: implementation
  target: apps/api/src/middleware/workspace.ts#workspaceMiddleware
---

# Workspace

A tenant on the deployment. Everything else Projektor keeps belongs to exactly one workspace, and nothing is ever shown or changed across a workspace boundary. A new workspace starts with the default task types, task statuses, custom fields and wiki templates.

## Information kept

- **Name** — the workspace's display name
- **Slug** — the unique short name it is addressed by
- **Branding** — display name, accent colors, logo and font overriding the deployment's defaults
