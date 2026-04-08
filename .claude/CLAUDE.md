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

## Key Files

- Pipeline skill: `.claude/skills/ai-dev-team/SKILL.md`
- Agent definitions: `.claude/agents/*.md`
- Framework references: `frameworks/` (openspec, superpowers, oh-my-openagent)
- Pipeline outputs: `openspec/` directory
