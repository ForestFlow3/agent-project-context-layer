# PROJECT CONTEXT

## 中文

这个目录保存项目的稳定上下文，供 human 和 coding agent 查看。

它是普通项目数据，不是宿主 agent 的指令文件。默认安装不会创建或修改 `AGENTS.md`、`AGENT.md`、`CLAUDE.md`、`.cursor/rules/` 或其他 instruction files。

### 文件

| 文件 | 用途 |
|---|---|
| `PROJECT_CONTEXT.md` | 项目目标、边界、当前状态、未决问题和来源映射。 |
| `AGENT_BRIEF.md` | 新 session 的快速交接摘要。 |
| `DECISIONS.md` | 已接受或发生变化的决策。 |
| `RISKS.md` | 已知风险和缓解方式。 |
| `TODO.md` | 当前下一步行动。 |

### 使用方式

开启或续接项目对话时，由用户明确要求 coding agent 读取本文件及上表文件。

完成有意义的工作后，只更新稳定项目状态。不要编造事实，也不要重写已有历史。

把本目录接入宿主 instruction file 是可选操作，必须先展示完整 patch，并取得用户明确批准。

## English

This directory stores durable project context for humans and coding agents to inspect.

It is ordinary project data, not a host-agent instruction file. Default setup does not create or modify `AGENTS.md`, `AGENT.md`, `CLAUDE.md`, `.cursor/rules/`, or other instruction files.

### Files

| File | Purpose |
|---|---|
| `PROJECT_CONTEXT.md` | Project goal, boundaries, current state, open questions, and source map. |
| `AGENT_BRIEF.md` | Fast handoff summary for a new session. |
| `DECISIONS.md` | Accepted or changed decisions. |
| `RISKS.md` | Known risks and mitigations. |
| `TODO.md` | Current next actions. |

### Usage

When starting or resuming project work, the user explicitly asks the coding agent to read this file and the files listed above.

After meaningful work, update only durable project state. Do not invent facts or rewrite history.

Connecting this directory to a host instruction file is optional and requires an exact patch preview plus explicit user approval.
