---
kind: primary
routes:
  web: Web app
steps:
- text: The User revokes one of their connected applications
  kind: actor
  actor: user
  entities:
  - {entity: connected-application, effect: reads, facts: [Application, Connected at]}
  contexts:
    web:
      place: web::workspace::connect-agent
- text: The Product withdraws the connected application's access
  kind: product
  actor: user
  entities:
  - {entity: connected-application, effect: removes}
  contexts:
    web:
      place: web::workspace::connect-agent
---

# Revoke a connected application

## Trigger

A person no longer wants an application acting for them.

## Outcome

The application can no longer reach the workspace as the User.
