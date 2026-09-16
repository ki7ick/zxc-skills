# zxc-skills

[English README](README.md)

一组面向 AI 编程 Agent 的可复用 Skill。

## 当前包含的 Skill

### `agent-working-principles`

用于指导 Agent 工作时的基本原则，包括基于事实判断、获取充分上下文、分析根因、进行架构层面的思考、保持表达简洁，以及在修改代码或文档前说明原因和方案。

### `human-readable-code-plan`

将代码设计、重构方案和改动清单整理成开发者易于理解、检查和执行的说明。

## 安装

查看仓库中的 Skill：

```bash
npx skills add ki7ick/zxc-skills --list
```

安装单个 Skill：

```bash
npx skills add ki7ick/zxc-skills --skill agent-working-principles
```

安装全部 Skill：

```bash
npx skills add ki7ick/zxc-skills --skill '*'
```

安装到指定 Agent 并设为全局可用：

```bash
npx skills add ki7ick/zxc-skills --skill '*' --agent cursor --global
```

如果不指定 Agent 或安装范围，CLI 可能会在安装过程中提示选择。

## 仓库结构

```text
skills/
├── agent-working-principles/
│   └── SKILL.md
└── human-readable-code-plan/
    └── SKILL.md
```

## 说明

Skill 是否自动加载取决于目标 Agent 的行为。安装 Skill 并不代表它一定会在每次对话中自动生效。如果某些原则需要对所有任务生效，并且目标 Agent 支持项目级或全局 instructions，建议同时配置对应的 instructions 文件。

