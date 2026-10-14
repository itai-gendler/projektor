---
availability:
- place: web::workspace
- place: mcp
domain: metrics
references:
- kind: code
  role: implementation
  target: apps/api/src/services/code-heatmap.ts#getCodeHeatmap
- kind: code
  role: implementation
  target: apps/web/src/islands/charts/CodeHeatmap.tsx
---

# View code heatmap

A member sees where work lands in the code, from file claim history: by how many issues claimed paths under each folder, or by how much contention each folder saw.
