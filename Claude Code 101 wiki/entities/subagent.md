---
title: Subagent
type: entity
category: other
---

# Subagent

**Type**: other

**Aliases**: Subagents

## Facts

- 用于代码审查，拥有独立 [[Context Window]]
- 可以将任务分解并在并行中运行组件任务
- 每个子代理在自己的隔离上下文窗口中操作
- 通过 [[Markdown]] 文件和 [[YAML]] frontmatter 定义

## Connections

- [[claude-code|Claude Code]] uses [[subagent|Subagent]]: Claude Code 可以使用 subagent 进行代码审查
- [[claude|Claude]] related-to [[subagent|Subagent]]: Claude 可以将任务委托给子代理进行分解和并行处理
- [[subagent|Subagent]] related-to [[context-window-management|Context Window Management]]: 子代理帮助管理上下文窗口，避免探索内容污染主开发功能
- [[subagent|Subagent]] related-to [[persistent-memory|Persistent Memory]]: 子代理支持持久化记忆功能，适合在同一项目上持续使用
- [[subagent|Subagent]] related-to [[skills-loading|Skills Loading]]: 子代理支持通过 skill 键加载技能到上下文中

## Sources

- [[7-code-review]]
- [[9-subagents]]
