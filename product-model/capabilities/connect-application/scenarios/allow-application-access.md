---
kind: primary
routes:
  web: Web app
steps:
- text: The User arrives at the consent page from an application's connector sign-in
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace::application-consent
- text: The User is a member of the workspace the application asks for
  kind: condition
  actor: user
  entities:
  - {entity: workspace, effect: reads, facts: [Name]}
  - {entity: workspace-membership, effect: reads, facts: [Role]}
  contexts:
    web:
      place: web::workspace::application-consent
- text: The User reads the application, the workspace, the access asked for and their own role, and allows access
  kind: actor
  actor: user
  entities:
  - {entity: connected-application, effect: reads, facts: [Application, Access]}
  - {entity: workspace, effect: reads, facts: [Name]}
  - {entity: workspace-membership, effect: reads, facts: [Role]}
  contexts:
    web:
      place: web::workspace::application-consent
- text: The Product records the connected application and returns the person to the application signed in
  kind: product
  actor: user
  entities:
  - {entity: connected-application, effect: creates, facts: [Application, Access, Connected at, Expires at]}
  contexts:
    web:
      place: web::workspace::application-consent
---

# Allow an application to reach the workspace

## Trigger

A person adds their workspace's MCP address to an application and signs in.

## Outcome

The application reaches the workspace as the User, within the User's own permissions.

## Edge cases

- A workspace the User is not a member of is refused on the page itself, without telling the application.
- A request carrying an agent's credential, or the anonymous public viewer, cannot allow access.
