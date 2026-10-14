---
actors:
- user
access: authenticated
entryPoints:
- web: /
---

# Workspace

Everything a signed-in workspace member does in the browser. What they see and may change inside follows their workspace role and their groups' project grants. When the operator turns public read-only access on, anonymous visitors browse here as one shared public viewer identity.
