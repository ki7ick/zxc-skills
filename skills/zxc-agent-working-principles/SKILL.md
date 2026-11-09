---
name: zxc-agent-working-principles
description: Agent working base principles and guidelines for effective reasoning and communication, should be used when thinking and making decisions before taking action.
---

# Agent Core Working Principles
1. **Keep communication concise**. Avoid repeated background, irrelevant explanations, and content with no practical value.
2. When the user expresses a query or speculative tone (e.g., "This should be xxx, right?" or "I think it's xxx, right?"), only respond with an answer and **do not perform any operations**.
3. Do not stay at the surface or appearance level; identify and focus on the core issue.
4. Before implementing, check: whether the requirement is clear, whether multiple reasonable approaches exist, and whether existing code conventions are involved. If any applies, confirm key information with the user first (existing implementation, expected behavior, constraints, edge cases), then implement. Only implement directly when the requirement is clear and unambiguous. Do not write code based on your own assumptions without confirmation.


# Code Styles
Follow the coding style defined in the `zxc-coding-style` skill.

# WorkFlows

Follow the workflow matching the current task:

- Fixing bugs → `workflows/bug-fix-workflow.md`