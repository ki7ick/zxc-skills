---
name: human-readable-code-plan
description: Turn code plans into human-readable, reviewable, and actionable change descriptions.
---

## Core Principle

Present code designs, refactoring plans, and change lists in a way that helps developers quickly understand, review, and execute them.

## Output Guidance

These are recommendations, not a fixed format. Adjust, combine, or omit them according to the complexity of the plan, the user's context, and the type of change.
See "Output Template Reference" for one possible structure, but do not follow it mechanically.

### Start with the big picture

Usually begin with a short summary or a list of the main changes. Add reasons when they are useful.

> Focus the summary on business or code-structure changes, not on the entire analysis process.

For example:

```text
Summary:
1. Keep task_type as the task execution key; do not treat it as appFeatureCode or the task name.
	> Based on the user's requirement: task_type !== appFeatureCode.
2. Remove the existing task-name derivation logic.
	> The old logic does not fit the new requirement.
3. Add independent task-name generation and persistence.
```

For a small plan, one sentence may be enough. For a larger plan, organize the summary by phase, module, or dependency without forcing numbered items.

### Organize around changes

Organize the explanation around the actual changes rather than repeating the analysis process. For important or potentially confusing changes, explain the relevant location, its current responsibility, why it needs to change, and the resulting behavior.

Do not provide isolated file names, line numbers, or function names. Connect each code location to its responsibility and the reason for the change.

Use headings, numbers, short paragraphs, or lists as appropriate. No fixed format is required.

### Use code examples to clarify

When code helps explain the change, use an appropriate form such as a diff, focused snippet, pseudocode, or flow diagram. Do not mechanically show every file as a diff.

Useful examples include:

- Important changes to interfaces, fields, or function calls.
- Data flow before and after the change.
- Core code that shows a change in responsibility.
- Behavioral differences that require user confirmation.

Omit unrelated implementation details and replace them with a short explanation. Examples should show only the important changes, not imply complete implementation.

For example:

```diff
- const taskName = getTaskNameByType(task.task_type);
+ const taskName = task.name;
```

```ts
// Example: show only the key flow
export async function generateTaskName(taskType: string) {
	const content = createTaskNameContent(taskType);
	await saveNameSnapshot(content);
	return generateByTimestamp();
}
```

Not every change needs code. Prefer prose, a flow diagram, or a data structure when it communicates the idea more clearly.

## Boundaries

- Write for developers who are making decisions or preparing to change code.
- Prioritize conclusions, changes, and impact; include only reasoning that is necessary for understanding or decisions.
- Choose headings, lists, tables, diffs, code snippets, or flow diagrams according to context.
- Do not treat the examples in this Skill as a required template.
- Follow any format or focus explicitly requested by the user.
- If an important part of the plan is uncertain, mark it as an open question instead of presenting it as confirmed.

## Output Template Reference

The following is one possible structure, not a fixed template or complete implementation.

Summary:

1. Keep task_type as the task execution key; do not treat it as appFeatureCode or the task name.
	> Based on the user's requirement: task_type !== appFeatureCode.

2. Remove the existing task-name derivation logic.
	> The old logic does not fit the new requirement.

3. Add independent task-name generation and persistence.

### 1. Adjust task creation

File: task/dbt.ts

This file creates task records, so generate the task name before writing the record to the database.

```diff
	 export async function addTask(taskArgs: AddTaskArgs) {
+   const name = await generateTaskName(taskArgs.taskType);

		return tx.task.create({
			data: {
				task_type: taskArgs.taskType,
+       name,
			},
		});
	}
```

After the change, the task name is fixed when the task is created. Later changes to the task-type mapping will not change the display name of historical tasks.

### 2. Adjust task details display

File: task/detail.tsx

The page only displays task data; it no longer derives the name from task_type.

```diff
- const name = getTaskNameByType(task.task_type);
+ const name = task.name;
```

Other logic unrelated to task-name display remains unchanged.

