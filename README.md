# AI Dev Team

An AI-powered development team orchestrator for Claude Code that coordinates three open-source frameworks through a 5-phase development pipeline.

## Overview

Inspired by the concept of autonomous AI development teams, this project integrates:

- **[OpenSpec](https://github.com/fission-ai/openspec)** - Spec-driven development framework for requirements and design documentation
- **[Superpowers](https://github.com/obra/superpowers)** - Engineering best practices and TDD workflow skills
- **[oh-my-openagent](https://github.com/code-yeongyu/oh-my-openagent)** - Multi-agent orchestration concepts (DAG scheduling, parallel execution)

These are coordinated by a custom **ai-dev-team** orchestrator skill adapted for the Claude Code environment.

## The 5-Phase Pipeline

```
Phase 1: Requirements Analysis  --> Clarify needs, document requirements
Phase 2: Technical Design       --> Architecture, tech stack, task breakdown
Phase 3: Task Orchestration     --> DAG analysis, agent assignment, parallel strategy
Phase 4: Parallel TDD Dev      --> Multiple agents implement tasks with TDD
Phase 5: Result Aggregation     --> Integration tests, spec verification, delivery
```

## Quick Start

### Prerequisites

- Claude Code installed and configured
- Node.js 20.19.0+ (for OpenSpec CLI)

### Setup

1. Clone this repository
2. Install OpenSpec CLI:
   ```bash
   npm install -g @fission-ai/openspec@latest
   ```

### Usage

In Claude Code, invoke the pipeline:

```
/ai-dev-team Build a REST API for a task management system
```

The orchestrator will guide you through all 5 phases, with approval gates between phases.

### Using Individual Agents

You can also use agents directly for specific tasks:

```
@requirements-analyst Analyze requirements for a user authentication system
@technical-designer Design the architecture for a chat application
@tdd-implementer Implement user registration with email validation
```

## Project Structure

```
.claude/
  agents/             # 6 specialized agent definitions
  skills/ai-dev-team/ # Core orchestrator skill
  CLAUDE.md           # Claude Code context
frameworks/
  openspec/           # OpenSpec framework (cloned)
  superpowers/        # Superpowers skills (cloned)
  oh-my-openagent/    # OmO framework (reference)
openspec/             # Pipeline output directory (created at runtime)
```

## Architecture

### Agent Roles

| Agent | Role | Phase |
|-------|------|-------|
| requirements-analyst | Product Manager | Phase 1 |
| technical-designer | Architect | Phase 2 |
| task-orchestrator | Tech Lead | Phase 3 |
| tdd-implementer | Developer | Phase 4 |
| code-reviewer | QA Engineer | Phase 4 |
| result-aggregator | Release Manager | Phase 5 |

### Framework Integration

- **OpenSpec**: Used natively for spec management (requirements, design, tasks)
- **Superpowers**: Skills referenced for TDD, brainstorming, code review methodologies
- **oh-my-openagent**: Concepts adapted (DAG scheduling, category-based routing, parallel execution) - not directly executable

## Acknowledgments

- Original concept: "AI Dev Team" by WeChat public account "TechIdler"
- OpenSpec by [fission-ai](https://github.com/fission-ai)
- Superpowers by [obra](https://github.com/obra)
- oh-my-openagent by [code-yeongyu](https://github.com/code-yeongyu)

## License

MIT
