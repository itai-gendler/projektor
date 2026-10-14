---
kind: primary
routes:
  web: Web app
steps:
- text: The User names a new token, picks its scope and optionally an expiry
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace::connect-agent
- text: The Product mints the API token for the workspace and shows its secret once, with the command that connects an agent with it
  kind: product
  actor: user
  entities:
  - {entity: api-token, effect: creates, facts: [Name, Scope, Created at, Expires at]}
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::connect-agent
---

# Mint an API token

## Trigger

An admin wants to connect a headless agent or a script.

## Outcome

A token exists; its secret is never shown again.

## Edge cases

- A request made with an agent's credential, or as the anonymous public viewer, is refused: tokens are minted only from a person's browser session.
