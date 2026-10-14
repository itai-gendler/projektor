---
kind: alternative
routes:
  web: Web app
steps:
- text: The User opens the code heatmap
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web::workspace::metrics
- text: The Product groups file claims one folder level below the chosen prefix, sized by how many distinct issues claimed there
  kind: product
  actor: user
  entities:
  - {entity: file-claim, effect: reads, facts: [Path, Claimed at]}
  - {entity: group, effect: reads, facts: []}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::metrics
---

# See where work lands

## Trigger

The User wants to see which parts of the code get the most work.

## Outcome

The User sees the busiest folders.
