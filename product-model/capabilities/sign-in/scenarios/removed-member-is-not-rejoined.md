---
kind: edge
routes:
  web: Web app
steps:
- text: The User signs in again after an owner removed them from a workspace
  kind: actor
  actor: user
  entities:
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace
- text: The deployment settings would otherwise add them back as an admin, by domain or by auto-join
  kind: condition
  actor: user
  entities:
  - {entity: deployment-settings, effect: reads, facts: [Admin emails, Workspace domain map, Auto-join role]}
  contexts:
    web:
      place: web::workspace
- text: The Product leaves the User without a workspace membership of that workspace
  kind: product
  actor: user
  entities:
  - {entity: workspace, effect: reads, facts: [Name]}
  - {entity: workspace-membership, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace
references:
- kind: code
  role: implementation
  target: apps/api/src/services/workspaces.ts#removeMember
- kind: code
  role: implementation
  target: apps/api/src/services/provisioning.ts#ensureUserProvisioned
---

# A removed member is not re-added by configuration

## Trigger

An owner has removed a person whom the deployment settings would add to the workspace.

## Outcome

The removal stands until someone invites the User again.
