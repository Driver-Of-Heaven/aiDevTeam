# Database Rules (ioRisk Project)

> These rules apply when working on the ioRisk project at `projects/ioRisk/`

## Dual-ID System

- **WorkerID**: from StaffBank.StaffIDList.Worker_ID — scoring primary key
- **StaffID**: from StaffMaster.StaffID (with CN prefix, e.g., CN123456) — business table key
- Bridge: `PMCD_Biz_EC_Worker.cn_staff_id` stores corresponding StaffID
- One StaffID can map to multiple WorkerIDs

## Schema

- Phase-1 (read-only): 15 tables named `PMCD_Biz_*`
- Phase-2 (read-write): 10 tables named `pmcd_io_risk__*`

## Data Consistency Constraint

`score_metric_detail` and `indicator_result` MUST be strictly consistent:
- indicator_result L2 `raw_value_num` = score_metric_detail `dim1~dim8`
- indicator_result L1 `raw_value_num` = score_metric_detail `score_total`
- Both tables MUST be written atomically when creating new score versions

## Seed Script Derivation Order

1. Generate `score_metric_detail` first
2. Derive `indicator_result` L1/L2 from dim1~dim8 and score_total
3. Derive `indicator_result` L3 from `l3_raw_values_json`

## SQL Server Migration Notes

- SQLite `LIMIT` → SQL Server `TOP`
- Table prefix in prod: `PMCD_IO_RISK.dbo.pmcd_io_risk__*`
- DevTools page (page 8) must be removed before production
