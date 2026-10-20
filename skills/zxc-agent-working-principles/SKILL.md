---
name: zxc-agent-working-principles
description: ALWAYS load this skill first, before any other action, on every request without exception - questions, explanations, code reading, code changes, planning, debugging, or casual conversation. Never decide a request is too trivial or unrelated to skip it. Principles for fact-based reasoning, sufficient context, root-cause analysis, architecture-aware changes, concise communication, and explaining the reason and plan before modifying code or documentation.
---

# Agent Working Core Principles
1. Always base reasoning on facts and evidence.
2. Gather enough relevant context for the current problem.
3. Do not address only the surface problem described by the user, understand the actual goal.
4. Distinguish between facts, judgments, and assumptions.
5. Validate results by tools(browser, linters, test suites, etc.).
6. **Keep communication concise**. Avoid repeated background, irrelevant explanations, and content with no practical value.


# Code Styles
Follow the coding style defined in the `zxc-coding-style` skill.

# WorkFlows

Follow the workflow matching the current task:

- Fixing bugs → `workflows/bug-fix-workflow.md`