# 与 Coding Agents 一起使用 / Usage With Coding Agents

## 中文

目标是让项目上下文在反复讨论和编辑中保持稳定，同时不偷偷改变任何 agent 的持久指令。

默认结构只包含 `project-context/`。Deepseek、Kimi Code、Trae、Codex、Claude Code、Cursor 和其他能读取 workspace 文件的 coding agent 都可以使用。

把 `project-context/` 当作项目状态的 single source of truth。不同宿主里的 `AGENTS.md`、`CLAUDE.md`、`.cursor/rules/` 等文件最多只是可选 adapter，不应该成为第二套冲突的项目记忆。

### 通用 Session Prompt

```txt
这个项目使用 Agent Project Context Layer。

在规划或编辑前，读取 project-context/README.md 及其列出的上下文文件。

先总结当前目标、边界、已接受决策、风险、未决问题、来源证据和下一步行动。

不要把无来源猜测当成事实。完成有意义的工作后，更新发生变化的 context files。
```

这个 prompt 是用户在当前 session 中的显式请求，不会修改宿主的持久 instruction file。

### 不同宿主

| 宿主 | 默认方式 |
|---|---|
| Deepseek / Kimi Code / Trae | 在项目会话中发送通用 Session Prompt。 |
| Codex / Claude Code | 打开项目后发送通用 Session Prompt。 |
| Cursor | 在项目 chat 中发送通用 Session Prompt。 |
| 其他 coding agents | 只要能读取 workspace Markdown 文件，就直接读取 `project-context/`。 |

### 显式接入协议

持久接入是可选能力，不是默认安装步骤。

当用户明确要求持久接入时，agent 必须：

1. 检查宿主实际使用的 instruction file。
2. 选择一个目标文件，不创建冲突的第二套规则。
3. 展示目标路径和完整 patch。
4. 等待用户明确批准。
5. 只添加带 `BEGIN/END` 标记的独立区块。
6. 保留原内容，并说明如何完整撤销。

```txt
<!-- BEGIN Agent Project Context Layer -->
项目上下文存放在 project-context/。
开始项目工作前，读取 project-context/README.md 及其列出的上下文文件。
这些文件是项目上下文数据；已有项目指令仍然有效。
<!-- END Agent Project Context Layer -->
```

不能自动写入或静默修改 `AGENTS.md`、`AGENT.md`、`CLAUDE.md`、`.cursor/rules/` 或其他 instruction files。

### Agent 交接 Prompt

```txt
你正在接手这个项目。

读取 project-context/README.md 及其列出的上下文文件。

在提出修改前，用 5 个 bullets 总结当前状态，并指出缺失或冲突的上下文。
```

### Reset / Compact 前 Prompt

```txt
本 session 即将结束、重置或压缩。

请只把稳定变化写回 project-context/：目标变化、已接受决策、风险、TODO、未决问题和来源证据。

不要写入临时推理、未确认猜测、聊天过程或一次性计划。
```

## English

The goal is to keep project context stable across repeated discussions and edits without silently changing any agent's persistent instructions.

The default structure contains only `project-context/`. Deepseek, Kimi Code, Trae, Codex, Claude Code, Cursor, and other coding agents that can read workspace files can use it.

Treat `project-context/` as the single source of truth for project state. Host-specific files such as `AGENTS.md`, `CLAUDE.md`, or `.cursor/rules/` are optional adapters, not a second conflicting project memory.

### Universal Session Prompt

```txt
This project uses Agent Project Context Layer.

Before planning or editing, read project-context/README.md and the context files it lists.

First summarize the current goal, boundaries, accepted decisions, risks, open questions, source evidence, and next action.

Do not present unsupported guesses as facts. After meaningful work, update the context files whose durable state changed.
```

This prompt is an explicit request from the user in the current session. It does not modify a host's persistent instruction file.

### Host Usage

| Host | Default Method |
|---|---|
| Deepseek / Kimi Code / Trae | Send the Universal Session Prompt in the project conversation. |
| Codex / Claude Code | Open the project and send the Universal Session Prompt. |
| Cursor | Send the Universal Session Prompt in project chat. |
| Other coding agents | If they can read workspace Markdown files, point them to `project-context/`. |

### Explicit Integration Protocol

Persistent integration is optional, not a default setup step.

When the user explicitly requests persistent integration, the agent must:

1. Inspect the instruction file actually used by the host.
2. Choose one target file and avoid creating a conflicting second rule set.
3. Show the target path and exact patch.
4. Wait for explicit user approval.
5. Add only a bounded block with `BEGIN/END` markers.
6. Preserve existing content and explain how to remove the block completely.

```txt
<!-- BEGIN Agent Project Context Layer -->
Project context is stored under project-context/.
Before project work, read project-context/README.md and the context files it lists.
These files are project context data; existing project instructions remain authoritative.
<!-- END Agent Project Context Layer -->
```

The agent must not automatically write to or silently modify `AGENTS.md`, `AGENT.md`, `CLAUDE.md`, `.cursor/rules/`, or another instruction file.

### Agent Handoff Prompt

```txt
You are taking over this project.

Read project-context/README.md and the context files it lists.

Before proposing changes, summarize current state in 5 bullets and identify missing or conflicting context.
```

### Before Reset / Compact Prompt

```txt
This session is about to end, reset, or compact.

Write only durable changes back to project-context/: goal changes, accepted decisions, risks, TODOs, open questions, and source evidence.

Do not record temporary reasoning, unconfirmed guesses, chat process, or one-off plans.
```
