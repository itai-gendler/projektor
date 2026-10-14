---
kind: alternative
routes:
  web: Web app
steps:
- text: The User opens the web app without signing in
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace
- text: The deployment settings turn public read-only access on
  kind: condition
  actor: user
  entities:
  - {entity: deployment-settings, effect: reads, facts: [Public read-only]}
  contexts:
    web:
      place: web::workspace
- text: The Product treats the visit as the shared public viewer, a viewer member of the default workspace in the Public viewers group
  kind: product
  actor: user
  entities:
  - {entity: user, effect: reads, facts: [Public viewer]}
  - {entity: workspace-membership, effect: reads, facts: [Role]}
  - {entity: group, effect: changes, facts: [Members]}
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace
- text: Only projects granted to the Public viewers group are listed, read-only
  kind: condition
  actor: user
  entities:
  - {entity: project-grant, effect: reads, facts: [Role]}
  - {entity: project, effect: reads, facts: [Name]}
  - {entity: group, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace
references:
- kind: code
  role: implementation
  target: apps/api/src/services/provisioning.ts#provisionPublicViewer
- kind: code
  role: implementation
  target: apps/api/src/services/access.ts#effectiveProjectRole
---

# An anonymous visitor browses as the public viewer

## Trigger

Someone without a Cloudflare Access session opens a deployment whose operator turned public read-only access on.

## Outcome

The visitor reads the projects published to the Public viewers group and can change nothing.
