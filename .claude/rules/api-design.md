# API Design Rules (ioRisk Project)

> These rules apply when working on the ioRisk project at `projects/ioRisk/`

## Endpoints

Backend listens on localhost:8765. All endpoints prefixed with `/api/`.

## Data Tables Routes

- `GET /api/tables/primary` — Phase-1 tables (read-only)
- `GET /api/tables/secondary` — Phase-2 tables (read-write)
- MUST use English keys `primary`/`secondary`, never Chinese or numeric
- Backend regex: `^/api/tables/([a-zA-Z0-9]+)$` with `.lower()`

## Iron Rule

All frontend data MUST come from backend API. No hardcoded business data in frontend.
Allowed exceptions: UI constants (colors, labels, placeholders).

## API Status Display

- Red "API 未连线" — backend not running
- Orange "API 已连线（模拟环境）" — db_mode=sqlite
- Green "API 已连线（生产环境）" — db_mode=sqlserver

## Version Filtering

All data-fetching endpoints accept `?version=xxx` parameter.
Global version controlled by `#global-version-select` dropdown via `onGlobalVersionChange(ver)`.
