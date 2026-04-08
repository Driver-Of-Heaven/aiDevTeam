# AI Dev Team - Project Context

## What Is This Project?

This is an AI-powered development team orchestrator that coordinates three open-source frameworks through a 5-phase development pipeline. Inspired by the "ai-dev-team" concept, adapted for Claude Code.

## Architecture: One Engine, Three Pillars

### Engine: ai-dev-team (Custom Skill)
- Location: `.claude/skills/ai-dev-team/SKILL.md`
- Role: Project manager that orchestrates the entire pipeline
- Invoke with: `/ai-dev-team [project description]`

### Pillar 1: OpenSpec (Requirements & Design)
- Source: `frameworks/openspec/` (GitHub: fission-ai/openspec)
- Role: Generates structured requirements, technical designs, and task breakdowns
- CLI installed globally: `@fission-ai/openspec`
- Used in: Phase 1 (Requirements) and Phase 2 (Design)

### Pillar 2: oh-my-openagent (Task Orchestration Concepts)
- Source: `frameworks/oh-my-openagent/` (GitHub: code-yeongyu/oh-my-openagent)
- Role: Reference for multi-agent orchestration patterns (DAG scheduling, category-based routing, parallel execution)
- Note: This is an OpenCode plugin, NOT directly executable. We extract and adapt its concepts.
- Used in: Phase 3 (Task Orchestration) - concepts only

### Pillar 3: Superpowers (Engineering Practices)
- Source: `frameworks/superpowers/` (GitHub: obra/superpowers)
- Role: SKILL.md files that enforce TDD, code review, and development best practices
- Used in: Phase 4 (Development) and throughout as quality gates

## Custom Agents

All agent definitions are in `.claude/agents/`:

| Agent | Phase | Model | Purpose |
|-------|-------|-------|---------|
| requirements-analyst | 1 | opus | Clarify and document requirements |
| technical-designer | 2 | opus | Architecture design + task decomposition |
| task-orchestrator | 3 | opus | DAG analysis + agent assignment |
| tdd-implementer | 4 | sonnet | TDD implementation of individual tasks |
| code-reviewer | 4 | sonnet | Code quality and spec compliance review |
| result-aggregator | 5 | opus | Integration testing + delivery report |

## Pipeline Output Files

All pipeline artifacts are stored in `openspec/`:
- `requirements.md` - Phase 1 output
- `design.md` - Phase 2 output
- `tasks.md` - Phase 2 output (task breakdown)
- `execution-plan.md` - Phase 3 output
- `delivery-report.md` - Phase 5 output

## Conventions

- All implementation follows TDD (Red-Green-Refactor)
- Each task has explicit acceptance criteria
- Tasks are grouped into dependency waves for parallel execution
- User approval gates between Phases 1-3
- Task complexity classification: quick (haiku), standard (sonnet), complex (opus)

---

## Managed Project: ioRisk (IRI)

### Overview

**IRI — Independence Risk Intelligence**
PwC CNHK Independence Office 员工独立性风险评分分析平台（二期）。
- Location: `projects/ioRisk/` (Git Submodule)
- GitHub: https://github.com/Driver-Of-Heaven/ioRisk
- Version: v1.20.0

### Tech Stack

- Frontend: React 19 + Vite + Ant Design 6 + TypeScript + Zustand (port 3000)
- Backend: FastAPI + Uvicorn (port 8765)
- DB (POC): SQLite `projects/ioRisk/backend/iri.db`
- DB (Prod): SQL Server — HOST:AAA, PORT:1800, DB:IO_RISK
- Testing: Vitest (frontend) + Pytest (backend)

### Quick Start (ioRisk)

```bash
# Backend
cd projects/ioRisk
python -m backend.seed.seed_db       # Initialize DB (first time)
python -m backend.main               # Start backend on :8765

# Frontend (separate terminal)
cd projects/ioRisk/frontend
npm install                          # First time only
npm run dev                          # Start frontend on :3000

# Tests
cd projects/ioRisk/frontend && npm test
cd projects/ioRisk && python -m pytest tests/backend/ -v
```

### Architecture

- Phase-1 DB (read-only): 15 tables `PMCD_Biz_*` from legacy PMCD system
- Phase-2 DB (read-write): 10 tables `pmcd_io_risk__*` for IRI scoring
- Dual-ID: WorkerID (scoring key) + StaffID (business key), bridged by `cn_staff_id`
- Vite proxy: `/api/*` → `http://localhost:8765`
- 8 Frontend pages: DataSource | DataFlow | DataTable | Staff | Analytics | Tasks | AI | DevTools

### Scoring Model

- 3-tier indicators: L1(2) → L2(8) → L3(12)
- Risk levels: score >= 70 (high), >= 40 (medium), < 40 (low)
- Correction factors: Partner/Director ×1.2, tenure<2yr ×0.7, repeat violation ×1.3

### Key Rules

See `.claude/rules/` for detailed rules:
- `api-design.md` — API endpoint conventions
- `database.md` — Dual-ID system, schema, data consistency
- `js-coding.md` — Forbidden/required coding patterns

### Detailed Specification

For comprehensive project instructions (17.5KB), see:
`projects/ioRisk/IRI_Project_Instructions.md`
