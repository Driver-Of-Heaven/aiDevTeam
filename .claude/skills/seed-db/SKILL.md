---
name: seed-db
description: Initialize or reset the ioRisk SQLite POC database by running the seed script. Use when DB is missing, corrupted, or schema changed.
disable-model-invocation: true
allowed-tools: Bash
---

# Database Initialization (ioRisk)

Reset and seed the ioRisk SQLite POC database:

1. Navigate to the ioRisk project: `cd projects/ioRisk`
2. Delete existing `backend/iri.db` if present
3. Run: `python -m backend.seed.seed_db`
4. Verify the database was created and contains expected tables:
   - 15 Phase-1 tables (PMCD_Biz_*)
   - 10 Phase-2 tables (pmcd_io_risk__*)
5. Spot-check record counts:
   - score_metric_detail should have ~70 rows
   - indicator_result should have ~1260 rows
   - indicator_definition should have 22 rows
6. Report results
