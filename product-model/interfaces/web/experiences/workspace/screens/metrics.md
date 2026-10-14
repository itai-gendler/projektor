---
entities:
- entity: issue
  shows: [Ready at, Started at, In review at, Done at, Review bounces]
- entity: issue-lease
  shows: [Release reason]
- entity: file-claim
  shows: [Path, Claimed at]
- entity: claim-conflict
  shows: [Path, Forced, Occurred at]
entryPoints:
- web: /metrics
references:
- kind: code
  role: implementation
  target: apps/web/src/islands/MetricsDashboard.tsx
- kind: code
  role: implementation
  target: apps/web/src/islands/charts/CodeHeatmap.tsx
---

# Metrics

A project's flow metrics, factory health signals and code heatmap.
