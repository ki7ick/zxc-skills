# zxc-skills

[中文说明](README.zh-CN.md)

A collection of reusable skills for AI coding agents.

## Included Skills

### `zxc-agent-working-principles`

Principles for fact-based reasoning, sufficient context, root-cause analysis, architecture-aware changes, concise communication, and explaining the reason and plan before modifying code or documentation.

### `zxc-coding-style`

TypeScript/React coding style rules: avoid complex ternaries, assign return expressions to named variables, extract multi-statement JSX event handlers into named functions.

### `zxc-human-readable-code-plan`

Turns code designs, refactoring plans, and change lists into descriptions that are easy for developers to understand, review, and execute.

## How They Work Together

`zxc-agent-working-principles` is the entry point: its description instructs the agent to load it before anything else, and it points at the other skills conditionally — `zxc-coding-style` for TypeScript/React work, `zxc-human-readable-code-plan` when a plan needs to be presented for review.

Task workflows live inside the skill they belong to and are named explicitly from its SKILL.md rather than discovered by scanning a directory. Currently one exists: `skills/zxc-agent-working-principles/workflows/bug-fix-workflow.md`, a five-step flow that fixes bugs from the root cause instead of symptom patches, with a fast path for trivial ones.

## Install

List available skills:

```bash
npx skills add ki7ick/zxc-skills --list
```

Install:

```bash
npx skills add ki7ick/zxc-skills
```

The CLI will prompt you to choose the target agent and installation scope.
