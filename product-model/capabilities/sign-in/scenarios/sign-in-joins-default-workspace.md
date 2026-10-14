---
kind: alternative
routes:
  web: Web app
steps:
- text: The User signs in through the deployment's Cloudflare Access sign-in for the first time
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace
- text: The deployment settings name an auto-join role and the User's email domain is not mapped to another workspace
  kind: condition
  actor: user
  entities:
  - {entity: deployment-settings, effect: reads, facts: [Auto-join role, Workspace domain map]}
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace
- text: The Product records the User
  kind: product
  actor: user
  entities:
  - {entity: user, effect: creates, facts: [Email, Name, Public viewer]}
  contexts:
    web:
      place: web::workspace
- text: The Product gives the User a workspace membership of the default workspace with the auto-join role
  kind: product
  actor: user
  entities:
  - {entity: workspace, effect: reads, facts: [Slug]}
  - {entity: workspace-membership, effect: creates, facts: [Role, Joined at]}
  contexts:
    web:
      place: web::workspace
- text: No group of the User's grants any project yet, so every project list shows access pending
  kind: condition
  actor: user
  entities:
  - {entity: group, effect: reads, facts: [Members]}
  - {entity: project, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace
references:
- kind: code
  role: implementation
  target: apps/api/src/services/provisioning.ts#ensureUserProvisioned
- kind: code
  role: implementation
  target: apps/web/src/islands/AccessPending.tsx
---

# Auto-join gives a new person the configured role

## Trigger

A person the operator has not invited signs in while auto-join is configured.

## Outcome

The User is a member of the default workspace but sees no project until an admin adds them to a group.

## Edge cases

- A person whose email domain is in the workspace domain map joins that workspace with the mapped role instead, and never the default workspace.
