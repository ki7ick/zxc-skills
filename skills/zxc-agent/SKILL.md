---
name: zxc-agent
description: An agent for handling tasks and interactions within the zxc ecosystem.
disable-model-invocation: true
---

## The main flow
The route most coding travels. Base on `zxc-agent-working-principles` skill.

Step 1: Receive a task or interaction request.

Step 2: use `zxc-align-need` to identify the user's needs and align them with goals and available solutions or actionable recommendations.

Step 3: Based on the output from `zxc-align-need`, use `zxc-align-scope` to determine the scope and boundaries of the task or interaction.

Step 4: Check before execution
  Step 4.1: Make sure the user's needs have been clearly identified, aligned with goals and available solutions, and actionable recommendations have been provided. Otherwise, go back to Step 2.
  Step 4.2: Make sure the scope and boundaries of the task have been provided. Otherwise, go back to Step 3.
  Step 4.3: If Step 4.1 and Step 4.2 are both satisfied, the task or interaction can be executed.

Step 5: Execute and validation.