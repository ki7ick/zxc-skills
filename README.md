# zxc-skills

[中文说明](README.zh-CN.md)

A small collection of reusable skills for AI coding agents.

## Included Skills

### `agent-working-principles`

Principles for fact-based reasoning, sufficient context, root-cause analysis, architecture-aware changes, concise communication, and explaining the reason and plan before modifying code or documentation.

### `human-readable-code-plan`

Turns code designs, refactoring plans, and change lists into clear, reviewable, and actionable descriptions for developers.

## Installation

List the available skills:

```bash
npx skills add ki7ick/zxc-skills --list
```

Install one skill:

```bash
npx skills add ki7ick/zxc-skills --skill agent-working-principles
```

Install both skills:

```bash
npx skills add ki7ick/zxc-skills --skill '*'
```

Install for a specific agent or globally:

```bash
npx skills add ki7ick/zxc-skills --skill '*' --agent cursor --global
```

The CLI may prompt you to choose the target agent and installation scope when those options are omitted.

## Repository Structure

```text
skills/
├── agent-working-principles/
│   └── SKILL.md
└── human-readable-code-plan/
    └── SKILL.md
```

## Notes

Skills are loaded according to the behavior of the target agent. Installing a skill does not necessarily make it active in every conversation. For principles that should apply to every task, use the target agent's project or global instructions mechanism when available.

