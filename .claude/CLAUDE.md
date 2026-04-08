# AI Dev Team - Claude Code Configuration

## Quick Start

To start a new project through the AI Dev Team pipeline:
```
/ai-dev-team [describe what you want to build]
```

## Available Agents

Use these agents directly if you want to run a specific phase:
- `requirements-analyst` - Gather and document requirements
- `technical-designer` - Create architecture and task breakdown
- `task-orchestrator` - Plan parallel execution strategy
- `tdd-implementer` - Implement a task with TDD
- `code-reviewer` - Review code quality and spec compliance
- `result-aggregator` - Verify integration and generate delivery report

## ioRisk Skills

- `seed-db` - Initialize/reset ioRisk SQLite database
- `recalc-score` - Trigger full employee score recalculation
- `check-js` - Run JS syntax check on HTML files

## Managed Projects

- **ioRisk** (IRI): `projects/ioRisk/` — PwC employee risk scoring platform (React + FastAPI)
  - Backend: `cd projects/ioRisk && python -m backend.main` (port 8765)
  - Frontend: `cd projects/ioRisk/frontend && npm run dev` (port 3000)
  - Detailed spec: `projects/ioRisk/IRI_Project_Instructions.md`

## Key Files

- Pipeline skill: `.claude/skills/ai-dev-team/SKILL.md`
- Agent definitions: `.claude/agents/*.md`
- Project rules: `.claude/rules/*.md` (api-design, database, js-coding)
- Framework references: `frameworks/` (openspec, superpowers, oh-my-openagent)
- Pipeline outputs: `openspec/` directory
