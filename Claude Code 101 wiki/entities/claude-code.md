---
title: Claude Code
type: entity
category: tool
---

# Claude Code

**Type**: tool

**Aliases**: claude

## Facts

- 一种代理编码工具，能够理解代码库、编辑文件、运行命令并集成现有开发工具。
- 在终端、[[Visual Studio Code]]、[[Claude Desktop app]] 和 [[JetBrains IDEs]] 中可用。
- 与 [[Claude.ai]] 不同，拥有直接访问用户文件、终端和整个代码库的能力。
- 使用 [[Skill]].md 文件来自动应用特定任务的知识
- 支持个人技能和项目技能存储
- [[AI Agent]] capable of connecting to external [[Tools]] and data sources via MCP
- Uses slash commands like /mcp inside a session
- [[Claude Code]] 的代码编辑器工具，支持 [[AI Agent]] 功能
- 结合了代理概念，包括代理循环、管理上下文窗口、工具和可配置的权限
- 不同于典型聊天应用，在终端内运行
- 支持在终端、IDE 或 Web 使用，功能最先在此发布
- 安装后可运行 [[Claude Code]] 命令，需经过初始设置步骤如选择主题和登录账户
- 在任意目录运行可访问该目录及其子文件夹
- 一个 AI 助手工具，用户像与任何 AI 助手一样与其对话。
- 支持自动接受（Auto-accept）和请求批准（Approval）两种模式以管理文件更改和命令执行权限。
- 提供 [[Plan Mode]] 功能，可通过 Shift + Tab 菜单进入，用于在代码修改前分析代码库和研究实现计划。
- 用于实现 Explore, Plan, Code, Commit 工作流的 AI 工具。
- 支持进入 [[Plan Mode]]，在编写代码前收集信息并制定实施计划。
- 拥有 [[Subagent]] 功能（如 code reviewer）。
- [[Claude Code]] 是 AI 编程助手工具
- 支持上下文管理功能
- 具有内置功能以加速 git 工作流
- 一个 AI 编程工具，通过读取 [[CLAUDE.md]] 文件获得关于项目的持久记忆。

## Connections

- [[claude-code|Claude Code]] related-to [[ai-agent|AI Agent]]: Claude Code 作为 AI Agent 运行，这是其核心差异化特征。
- [[claude-code|Claude Code]] related-to [[claude-ai|Claude.ai]]: 与 Claude.ai 不同，Claude Code 拥有直接访问文件、终端和整个代码库的能力，无需复制粘贴。
- [[claude-code|Claude Code]] related-to [[skill|Skill]]: Claude Code 使用技能来自动应用特定任务的知识，无需重复解释团队标准或偏好格式。
- [[hooks|/hooks]] related-to [[claude-code|Claude Code]]: Hooks 是 Claude Code 生命周期管理的功能
- [[claude-code|Claude Code]] uses [[agentic-loop|Agentic Loop]]: 通过代理循环机制工作，包括收集上下文、执行操作和验证结果
- [[claude-code|Claude Code]] related-to [[context-window|Context Window]]: 拥有并管理上下文窗口，达到限制后自动压缩
- [[claude-code|Claude Code]] uses [[tools|Tools]]: 利用工具执行代码和获取信息以完成任务
- [[claude-code|Claude Code]] related-to [[permissions|Permissions]]: 支持多种可配置的权限模式，包括默认行为、自动接受和计划模式
- [[terminal|Terminal]] related-to [[claude-code|Claude Code]]: Claude Code 在终端内运行
- [[claude-code|Claude Code]] related-to [[terminal|Terminal]]: 支持通过 curl/Invoke-RestMethod/winget/brew install 安装，功能最先在此发布
- [[claude-code|Claude Code]] related-to [[visual-studio-code|Visual Studio Code]]: 提供扩展，体验类似终端，可配置不使用 UI
- [[claude-code|Claude Code]] related-to [[jetbrains-ides|JetBrains IDEs]]: 提供插件，重启后显示 Logo，打开侧边栏终端体验
- [[claude-code|Claude Code]] related-to [[claude-desktop-app|Claude Desktop app]]: 顶部有'Code'切换按钮，可工作于特定文件夹，更改权限，云环境支持
- [[claude-code|Claude Code]] related-to [[github|GitHub]]: Web 版仅限于 GitHub 仓库访问
- [[anthropic|Anthropic]] related-to [[claude-code|Claude Code]]: 开发 Claude Code 扩展的组织
- [[claude-code|Claude Code]] related-to [[plan-mode|Plan Mode]]: Claude Code 包含 Plan Mode 功能，用户可通过 Shift + Tab 菜单进入该模式。
- [[claude-code|Claude Code]] related-to [[permissions|Permissions]]: Claude Code 的操作受 Permissions 约束，用户可选择自动接受或请求批准模式来管理权限。
- [[claude-code|Claude Code]] related-to [[ai-agent|AI Agent]]: Claude Code 是一个 AI Agent，用户像与任何 AI 助手一样与其对话以完成编程任务。
- [[claude-code|Claude Code]] related-to [[plan-mode|Plan Mode]]: Claude Code 支持进入 Plan Mode，在编写代码前收集信息并制定实施计划。
- [[claude-md|CLAUDE.md]] related-to [[claude-code|Claude Code]]: 用户可将解决方案保存到 CLAUDE.md 文件，以便 Claude 在后续遇到类似问题时参考。
- [[claude-code|Claude Code]] uses [[context-window|Context Window]]: Claude Code 使用 Context Window 作为其工作记忆
- [[claude-code|Claude Code]] uses [[subagent|Subagent]]: Claude Code 可以使用 subagent 进行代码审查

## Sources

- [[1-what-is-claude-code]]
- [[10-what-are-skills]]
- [[11-mcp]]
- [[12-hooks]]
- [[2-how-claude-code-works]]
- [[3-installing-claude-code]]
- [[4-your-first-prompt]]
- [[5-the-explore-plan-code-commit-workflow]]
- [[6-context-management]]
- [[7-code-review]]
- [[8-the-claude-md-file]]
