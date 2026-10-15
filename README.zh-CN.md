# zxc-skills

[English README](README.md)

一组面向 AI 编程 Agent 的可复用 Skill。

## 当前包含的 Skill

### `zxc-agent-working-principles`

用于指导 Agent 工作时的基本原则，包括基于事实判断、获取充分上下文、分析根因、进行架构层面的思考、保持表达简洁，以及在修改代码或文档前说明原因和方案。

### `zxc-coding-style`

TypeScript/React 编码风格规则：避免复杂三元表达式，return 前先赋值给具名变量，把多语句 JSX 事件处理函数提取为具名函数。

### `zxc-human-readable-code-plan`

将代码设计、重构方案和改动清单整理成开发者易于理解、检查和执行的说明。

## 协作关系

`zxc-agent-working-principles` 是入口：它的 description 要求 Agent 在任何动作之前先加载它，并由它按需指向其他 skill——TypeScript/React 代码遵循 `zxc-coding-style`，需要向用户呈现方案时使用 `zxc-human-readable-code-plan`。

任务工作流放在所属 skill 目录内，由该 SKILL.md 显式点名，而不是让 Agent 扫目录去找。目前有一个：`skills/zxc-agent-working-principles/workflows/bug-fix-workflow.md`，五步流程按根因而非症状修 bug，并为简单 bug 留有跳过中间步骤的快速路径。

## 安装

查看可用的 Skills：

```bash
npx skills add ki7ick/zxc-skills --list
```

安装：
```bash
npx skills add ki7ick/zxc-skills
```
CLI 会在安装过程中提示选择指定agent 或 范围。

