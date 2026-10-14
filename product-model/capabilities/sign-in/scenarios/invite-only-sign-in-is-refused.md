---
kind: validation
routes:
  web: Web app
steps:
- text: The User signs in through the deployment's Cloudflare Access sign-in without having been invited
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace
- text: The deployment settings set no auto-join role and do not map the User's email domain
  kind: condition
  actor: user
  entities:
  - {entity: deployment-settings, effect: reads, facts: [Auto-join role, Workspace domain map]}
  contexts:
    web:
      place: web::workspace
- text: The Product records the User but gives them no workspace membership and refuses every workspace page as forbidden
  kind: product
  actor: user
  entities:
  - {entity: user, effect: creates, facts: [Email, Name, Public viewer]}
  - {entity: workspace-membership, effect: reads, facts: []}
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace
---

# Invite-only deployment refuses an uninvited person

## Trigger

A person Cloudflare Access admits signs in to an invite-only deployment.

## Outcome

The User is known to Projektor but reaches no workspace until an admin invites them.
