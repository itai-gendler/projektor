---
kind: person
acts: external
relations:
- entity: workspace-membership
  verb: holds
  cardinality: one-to-many
- entity: ai-agent
  verb: connects
  cardinality: one-to-many
- entity: comment
  verb: writes
  cardinality: one-to-many
- entity: issue
  verb: is assigned
  cardinality: one-to-many
- entity: connected-application
  verb: authorizes
  cardinality: one-to-many
- entity: api-token
  verb: mints
  cardinality: one-to-many
- entity: share-link
  verb: creates
  cardinality: one-to-many
- entity: wiki-draft
  verb: drafts
  cardinality: one-to-many
- entity: wiki-watch
  verb: keeps
  cardinality: one-to-many
- entity: wiki-notification
  verb: receives
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: apps/api/src/middleware/auth.ts#authMiddleware
- kind: code
  role: implementation
  target: apps/api/src/services/provisioning.ts#ensureUserProvisioned
---

# User

A person who signs in to the deployment. Facts that belong to the person whatever their role live here; the role they hold in each workspace lives on their workspace membership.

## Information kept

- **Email** — the address Cloudflare Access signs them in with
- **Name** — the display name, taken from the local part of the email
- **Public viewer** — whether this is the one shared identity anonymous visitors use while public read-only access is on
