---
kind: primary
routes:
  web: Web app
steps:
- text: The User signs in through the deployment's Cloudflare Access sign-in with an email listed in the deployment's admin emails
  kind: actor
  actor: user
  entities:
  - {entity: deployment-settings, effect: reads, facts: [Admin emails]}
  contexts:
    web:
      place: web::workspace
- text: No workspace with the default workspace's slug exists yet
  kind: condition
  actor: user
  entities:
  - {entity: deployment-settings, effect: reads, facts: [Default workspace]}
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace
- text: The Product records the User and creates the default workspace with its default task statuses, types, custom fields and wiki templates, making the User its owner through a workspace membership
  kind: product
  actor: user
  entities:
  - {entity: user, effect: creates, facts: [Email, Name, Public viewer]}
  - {entity: workspace, effect: creates, facts: [Name, Slug]}
  - {entity: workspace-membership, as: own-membership, effect: creates, facts: [Role, Joined at], with: workspace}
  - {entity: task-status, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace
- text: The Product makes the User owner of every other workspace on the deployment
  kind: product
  actor: user
  entities:
  - {entity: workspace-membership, as: other-memberships, effect: changes, facts: [Role]}
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace
---

# First admin sign-in creates the default workspace

## Trigger

The first person on the admin email list signs in to a fresh deployment.

## Outcome

The default workspace exists and the User owns it and every other workspace.

## Edge cases

- An admin who signs in later becomes owner of every existing workspace, including ones other people created.
