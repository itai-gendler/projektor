---
kind: primary
routes:
  web: Web app
steps:
- text: The User switches the code heatmap to contention
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace::metrics
- text: The Product groups the claim conflicts one folder level below the chosen prefix and ranks them
  kind: product
  actor: user
  entities:
  - {entity: claim-conflict, effect: reads, facts: [Path, Forced, Occurred at]}
  - {entity: group, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::metrics
---

# See where agents collide

## Trigger

The User wonders how the work is being sliced.

## Outcome

The User sees which folders agents keep colliding on.
