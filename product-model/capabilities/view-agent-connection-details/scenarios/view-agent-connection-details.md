---
kind: primary
routes:
  web: Web app
steps:
- text: The User opens Connect Agent
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace::connect-agent
- text: The Product shows the workspace's MCP address and the command that adds it to the User's agent
  kind: product
  actor: user
  entities:
  - {entity: workspace, effect: reads, facts: [Slug]}
  contexts:
    web:
      place: web::workspace::connect-agent
---

# Copy the MCP address

## Trigger

A member wants their agent in the workspace.

## Outcome

The User can add the workspace to their agent and sign in.
