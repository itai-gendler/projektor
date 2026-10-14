---
availability:
- place: web::workspace
- place: mcp
domain: metrics
references:
- kind: code
  role: implementation
  target: apps/api/src/services/flow-metrics.ts#getFlowMetrics
- kind: doc
  role: intent
  target: apps/docs/src/content/docs/agents/flow-metrics.md
  title: Flow metrics
---

# View flow metrics

A member reads a project's flow metrics: lead time from ready to done, cycle time from started to done, review latency, aging work, WIP over time, and factory health signals such as lease expiries and review rejections.
