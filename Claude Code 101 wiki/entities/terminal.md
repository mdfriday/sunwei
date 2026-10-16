---
title: Terminal
type: entity
category: other
---

# Terminal

**Type**: other

## Facts

- [[Claude Code]] 可用的运行环境，可执行构建脚本、测试和安装包等命令。
- Used to run the '[[Claude Code]] mcp add' command from the [[Terminal]]
- [[Claude Code]] 运行在终端内
- macOS、Linux 或 WSL 下推荐使用 curl 命令安装，支持 Invoke-RestMethod/[[winget]]/[[Homebrew]] install
- [[Homebrew]] 和 [[winget]] 方法不支持自动更新

## Connections

- [[terminal|Terminal]] related-to [[claude-code|Claude Code]]: Claude Code 在终端内运行
- [[claude-code|Claude Code]] related-to [[terminal|Terminal]]: 支持通过 curl/Invoke-RestMethod/winget/brew install 安装，功能最先在此发布

## Sources

- [[1-what-is-claude-code]]
- [[11-mcp]]
- [[2-how-claude-code-works]]
- [[3-installing-claude-code]]
