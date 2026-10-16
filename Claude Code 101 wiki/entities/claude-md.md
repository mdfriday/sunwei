---
title: CLAUDE.md
type: entity
category: place
---

# CLAUDE.md

**Type**: place

**Aliases**: 项目配置文件, 入职脚本

## Facts

- 用于保存解决方案或提示词的文件。
- 用户可将解决相同问题的方案保存到该文件，以便 [[Claude Code]] 在后续遇到类似问题时参考。
- 用于存储跨会话需要记住的信息
- 包含命令、重要说明和架构部分
- 存储 [[Subagent]] 配置和 Slack MCP 服务器信息
- 一个 [[Markdown]] 文件，添加到项目根目录，[[Claude Code]] 每次启动会话时自动读取它。

## Connections

- [[claude-md|CLAUDE.md]] related-to [[claude-code|Claude Code]]: 用户可将解决方案保存到 CLAUDE.md 文件，以便 Claude 在后续遇到类似问题时参考。
- [[claude-md|CLAUDE.md]] related-to [[context-window|Context Window]]: 将需要跨会话记住的信息存储在 CLAUDE.md 中，避免重复发现内容消耗上下文空间
- [[claude-md|CLAUDE.md]] related-to [[context-window|Context Window]]: CLAUDE.md 文件的内容被附加到提示词中，为模型提供项目上下文。
- [[claude-md|CLAUDE.md]] related-to [[git-workflow|Git workflow]]: 可以将 CLAUDE.md 提交到版本控制中，实现团队共享记忆。
- [[readme-md|README.md]] related-to [[claude-md|CLAUDE.md]]: 在 CLAUDE.md 中使用 @ 符号引用 README.md 文件以获取更多项目信息。

## Sources

- [[5-the-explore-plan-code-commit-workflow]]
- [[6-context-management]]
- [[7-code-review]]
- [[8-the-claude-md-file]]
