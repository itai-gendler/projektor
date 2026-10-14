---
kind: primary
routes:
  web: Web app
steps:
- text: The User revokes an API token
  kind: actor
  actor: user
  entities:
  - {entity: api-token, effect: reads, facts: [Name, Last used at]}
  contexts:
    web:
      place: web::workspace::connect-agent
- text: The Product deletes the API token; agents using it are refused from their next request
  kind: product
  actor: user
  entities:
  - {entity: api-token, effect: removes}
  contexts:
    web:
      place: web::workspace::connect-agent
---

# Revoke an API token

## Trigger

A token leaked or is no longer needed.

## Outcome

The token no longer authenticates anything.
