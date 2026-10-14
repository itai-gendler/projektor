---
kind: primary
routes:
  web: Web app
steps:
- text: The User uploads a screenshot to an issue
  kind: actor
  actor: user
  entities:
  - {entity: issue, effect: reads, facts: [Title]}
  contexts:
    web:
      place: web::workspace::issue
- text: The file is at most 50 MB, of an allowed type, and fits in the workspace's storage quota
  kind: condition
  actor: user
  entities:
  - {entity: deployment-settings, effect: reads, facts: [Storage quota]}
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::issue
- text: The Product stores the file and attaches it to the issue
  kind: product
  actor: user
  entities:
  - {entity: attachment, effect: creates, facts: [Kind, File name, Content type, Size, Attached at]}
  - {entity: issue, effect: reads, facts: []}
  contexts:
    web:
      place: web::workspace::issue
---

# Attach a file to an issue

## Trigger

Something about an issue is easier to show than describe.

## Outcome

The file is listed on the issue and images show inline.
