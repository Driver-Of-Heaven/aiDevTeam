---
name: recalc-score
description: Trigger full employee score recalculation via the ioRisk backend API. Creates a new score version.
disable-model-invocation: true
allowed-tools: Bash
---

# Recalculate All Scores (ioRisk)

Trigger a full recalculation of employee risk scores:

1. Confirm the ioRisk backend server is running: `curl http://localhost:8765/api/health`
2. Call recalculation API: `curl -X POST http://localhost:8765/api/dev/recalc-and-score -H "Content-Type: application/json" -d "{}"`
3. Verify new version was created: `curl http://localhost:8765/api/score/versions`
4. Check data consistency between score_metric_detail and indicator_result
5. Report: new version ID, total employees scored, any anomalies
