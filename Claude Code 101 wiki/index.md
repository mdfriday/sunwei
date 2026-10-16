---
title: Knowledge Base Index
---

# Knowledge Base

**Last Updated**: 2026-05-22T07:51:50.195Z

## Statistics

- **Entities**: 31
- **Concepts**: 33
- **Connections**: 55
- **Sources**: 12

## Entities

- [[from-pr|--from-pr]] - 用于将会话链接到 PR 以便后续恢复工作 (1 source)
- [[claude-settings-json|.claude/settings.json]] - 用于配置 Hooks 的配置文件，位于 .claude 目录下 (1 source)
- [[clear|/clear]] - 完全从头开始的新会话命令 (1 source)
- [[commit-push-pr|/commit-push-pr]] - 处理 commit, push, PR creation 全流程 (1 source)
- [[compact|/compact]] - 手动触发上下文压缩的命令 (1 source)
- [[context|/context]] - 检查上下文状态的命令 (1 source)
- [[hooks|/hooks]] - 在 Claude Code 中配置 Hook 的 Slash Command (1 source)
- [[anthropic|Anthropic]] - Claude Code 扩展的开发者 (1 source)
- [[aws|AWS]] - CLI tool 'aws' available as context-efficient alternative to MCP tools (1 source)
- [[claude|Claude]] - 可以委托任务给子代理进行分解和并行处理 (1 source)
- [[claude-desktop-app|Claude Desktop app]] - Claude Code 可用的集成环境之一。 (2 sources)
- [[claude-ai|Claude.ai]] - 用户可能之前使用过的平台。 (2 sources)
- [[github|GitHub]] - CLI tool 'gh' available as context-efficient alternative to MCP tools (2 sources)
- [[jetbrains-ides|JetBrains IDEs]] - Claude Code 可用的集成环境之一。 (2 sources)
- [[linear|Linear]] - Project management service with MCP server support for retrieving issue details (1 source)
- [[markdown|Markdown]] - 用于定义子代理的格式 (1 source)
- [[readme-md|README.md]] - 项目文档，可以通过 @ 符号在 CLAUDE.md 中被引用以获取更多项目信息。 (1 source)
- [[subagent|Subagent]] - 用于代码审查，拥有独立 context window (2 sources)
- [[terminal|Terminal]] - Claude Code 可用的运行环境，可执行构建脚本、测试和安装包等命令。 (4 sources)
- [[visual-studio-code|Visual Studio Code]] - Claude Code 可用的集成环境之一。 (2 sources)
- [[vs-code|VS Code]] - 可以在 VS Code 中打开查看 CLAUDE.md 文件。 (1 source)
- [[yaml|YAML]] - frontmatter 用于定义子代理配置 (1 source)

### Place

- [[claude-skills|.claude/skills]] - 个人技能存放在 home directory，跟随所有项目 (1 source)
- [[claude-md|CLAUDE.md]] - 用于保存解决方案或提示词的文件。 (4 sources)

### Tool

- [[claude-code|Claude Code]] - 一种代理编码工具，能够理解代码库、编辑文件、运行命令并集成现有开发工具。 (11 sources)
- [[claude-in-chrome-extension|Claude in Chrome extension]] - 允许 Claude Code 控制浏览器标签页以直接测试 UI 的工具。 (1 source)
- [[context7|Context7]] - Provides a docs MCP server to look up latest shadcn/ui documentation (1 source)
- [[gofmt|gofmt]] - Go 语言项目的代码格式化工具 (1 source)
- [[homebrew|Homebrew]] - macOS/Linux/WSL 安装方式，不支持自动更新 (1 source)
- [[prettier|Prettier]] - 用于 TypeScript 等语言的代码格式化工具 (1 source)
- [[winget|winget]] - Windows 安装方式，不支持自动更新 (1 source)

## Concepts

- [[agentic-coding|Agentic Coding]] - 一种代理编码工具的方法论，能够理解代码库、编辑文件、运行命令并连接外部工具以帮助用户更快完成任务。 (2 sources)
- [[agentic-loop|Agentic Loop]] - 用户输入提示后，模型收集上下文、执行操作并验证结果，若未达成目标则循环重试的过程 (1 source)
- [[ai-agent|AI Agent]] - 能够与其环境交互并执行操作以完成既定目标的软件。核心是大型语言模型在实时循环中运行，可以访问工具、外部服务或其他 AI 代理以帮助达成目标。 (6 sources)
- [[approval-mode|Approval mode]] - 一种权限模式，Claude 每次想要编辑文件或运行命令时都会询问用户的明确许可。 (2 sources)
- [[auto-accept-mode|Auto-accept mode]] - 一种权限模式，文件更改会自动批准，但命令仍然需要用户许可。 (2 sources)
- [[blocking|Blocking]] - 通过 Hook 阻止工具调用的能力，用于强制执行安全规则 (1 source)
- [[code-review|Code review]] - 使用 subagent 进行无偏见的代码审查，不编辑文件 (1 source)
- [[compaction|Compaction]] - 当接近上下文限制时自动压缩的过程，总结重要细节并移除不必要的工具调用结果以释放空间 (1 source)
- [[context-window|Context Window]] - AI 模型的工作记忆。它可以容纳大量内容，但无法一次性容纳所有内容。在代理方面，Claude 会战略性地在代码库中定位答案，而不是加载全部内容。 (6 sources)
- [[context-window-management|Context Window Management]] - 管理上下文窗口大小，避免探索过程中发现的内容污染主要开发功能 (1 source)
- [[deterministic|Deterministic]] - 指系统行为总是执行，没有例外，与提示词不同 (1 source)
- [[explore-plan-code-and-commit-workflow|Explore, Plan, Code, and Commit workflow]] - 使用 Claude Code 进行有效开发的核心工作流：探索、计划、编码和提交。避免直接让 Claude 写代码以减少后期修正。 (1 source)
- [[git-workflow|Git workflow]] - 将 CLAUDE.md 提交到版本控制中，以便团队成员共享和受益，实现团队记忆共享。 (2 sources)
- [[hooks|Hooks]] - 在 Claude Code 生命周期特定点运行命令的机制，确保行为是确定性的（deterministic） (1 source)
- [[isolated-context-window|Isolated Context Window]] - 每个子代理在自己的隔离上下文窗口中操作，不污染主上下文 (1 source)
- [[mcp-servers|MCP Servers]] - Model Context Protocol 服务器，默认将所有可用工具加载到上下文中 (1 source)
- [[model-context-protocol|Model Context Protocol]] - 开放标准，让 Claude Code 能够连接到外部工具和数据源 (1 source)
- [[notification|Notification]] - Hook 事件类型之一，当 Claude 发送通知时运行 (1 source)
- [[parallel-task-execution|Parallel Task Execution]] - 子代理与主代理并行运行，各自拥有独立的上下文窗口 (1 source)
- [[permissions|Permissions]] - 可配置的权限模式，包括默认行为（编辑前询问）、自动接受（编辑不询问但命令需批准）和计划模式（只读工具先制定计划） (3 sources)
- [[persistent-memory|Persistent Memory]] - CLAUDE.md 文件赋予 Claude Code 关于项目的持久记忆，解决每次打开会话时重新探索代码库和依赖的问题。 (2 sources)
- [[plan-mode|Plan Mode]] - Claude 无法编辑文件，仅读取文件以收集信息并制定实施计划的模式。这是进行 Explore 和 Plan 阶段的最佳方式。 (2 sources)
- [[posttooluse|PostToolUse]] - Hook 事件类型之一，在工具调用完成后运行 (1 source)
- [[pretooluse|PreToolUse]] - Hook 事件类型之一，在工具调用之前运行 (1 source)
- [[session-linking|Session Linking]] - 将会话链接到 PR 以便后续恢复工作 (1 source)
- [[skill|Skill]] - 一个 markdown 文件，教导 Claude 如何一次性做某事，并在相关时自动应用该知识。 (2 sources)
- [[skills|Skills]] - 类似 MCP 服务器的功能但不预先将所有内容加载到上下文中 (1 source)
- [[skills-loading|Skills Loading]] - 通过 skill 键将技能加载到子代理中，整个技能被加载到上下文中 (1 source)
- [[slash-command|Slash Command]] - 使用斜杠命令（如 /init）来执行特定操作，例如生成 CLAUDE.md 文件。 (3 sources)
- [[stop|Stop]] - Hook 事件类型之一，当 Claude 完成响应时运行 (1 source)
- [[subagents|Subagents]] - 与主代理并行运行的子代理，拥有完全独立的上下文窗口 (1 source)
- [[tools|Tools]] - 代理工作的骨干，让 Claude Code 确定何时执行代码（如文件读取、网络搜索）以完成任务 (3 sources)
- [[userpromptsubmit|UserPromptSubmit]] - Hook 事件类型之一，当用户提交提示词时运行 (1 source)

## Sources

- [[9-subagents]] -  (2026-05-22, 4 entities, 5 concepts)
- [[8-the-claude-md-file]] -  (2026-05-22, 4 entities, 4 concepts)
- [[7-code-review]] -  (2026-05-22, 5 entities, 3 concepts)
- [[6-context-management]] -  (2026-05-22, 5 entities, 5 concepts)
- [[5-the-explore-plan-code-commit-workflow]] -  (2026-05-22, 3 entities, 4 concepts)
- [[4-your-first-prompt]] -  (2026-05-22, 1 entities, 6 concepts)
- [[3-installing-claude-code]] -  (2026-05-22, 10 entities, 3 concepts)
- [[2-how-claude-code-works]] -  (2026-05-22, 2 entities, 5 concepts)
- [[12-hooks]] -  (2026-05-22, 5 entities, 8 concepts)
- [[11-mcp]] -  (2026-05-22, 6 entities, 5 concepts)
- [[10-what-are-skills]] -  (2026-05-22, 2 entities, 5 concepts)
- [[1-what-is-claude-code]] -  (2026-05-22, 6 entities, 3 concepts)

## Quick Links

- [[GLOSSARY]]
- [[log]]
