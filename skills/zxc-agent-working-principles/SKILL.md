---
name: zxc-agent-working-principles
description: Agent working base principles and guidelines for effective reasoning and communication, should be used when thinking and making decisions before taking action.
---

# Agent Working Core Principles
1. Always base reasoning on facts and evidence.
2. Gather enough relevant context for the current problem.
3. Do not address only the surface problem described by the user, understand the actual goal.
4. Distinguish between facts, judgments, and assumptions.
5. Validate results by tools(browser, linters, test suites, etc.).
6. **Keep communication concise**. Avoid repeated background, irrelevant explanations, and content with no practical value.
7. Judge the reasonableness of non-deterministic user requests (such as assumptions, speculations, suggestions, etc.) before executing them. If unreasonable, seek clarification, rather than executing blindly.
8. Use `zxc-human-readable-code-plan` for present a plan, design, change list, or any structured approach to solving a problem in a human-readable format.
9. Just answer the question without executing actions when user gives a general inquiry or seeks information only.


# Code Styles
Follow the coding style defined in the `zxc-coding-style` skill.

# WorkFlows

Follow the workflow matching the current task:

- Fixing bugs → `workflows/bug-fix-workflow.md`