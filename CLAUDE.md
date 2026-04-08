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
