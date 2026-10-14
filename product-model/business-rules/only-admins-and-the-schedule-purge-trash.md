---
appliesTo:
- type: entity
  id: wiki-page
  effect: removes
permits:
- related: [{verb: keeps, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {entity: workspace-membership, fact: Role, is: Owner}
- related: [{verb: keeps, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: workspace-membership, fact: Role, is: Owner}
  - {entity: ai-agent, fact: Scope, is: Read and write}
- related: [{verb: keeps, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}]
  when:
  - {entity: workspace-membership, fact: Role, is: Admin}
- related: [{verb: keeps, entity: workspace}, {verb: admits, entity: workspace-membership}, {verb: holds, entity: user}, {verb: connects, entity: ai-agent}]
  when:
  - {entity: workspace-membership, fact: Role, is: Admin}
  - {entity: ai-agent, fact: Scope, is: Read and write}
- unattended: true
references:
- kind: code
  role: implementation
  target: apps/api/src/services/wiki.ts#purgeExpiredWikiPages
- kind: code
  role: implementation
  target: apps/api/src/index.ts#scheduled
---

# Only workspace owners and admins, and the daily schedule, purge the wiki trash

Purging pages that have been in the trash for 30 days needs the Owner or Admin workspace role; Projektor also purges them itself every day.
