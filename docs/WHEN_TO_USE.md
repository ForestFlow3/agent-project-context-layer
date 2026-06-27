# When To Use

## 中文

Agent Project Context Layer 适合在新项目启动时建立一层可持续维护的项目上下文。

核心问题不是“让多个 agent 共享同一份资料”，而是用户和 coding agent 反复讨论项目后，项目目标、边界、决策、风险和下一步容易漂移。

### 适合的场景

- 新建一个由 coding agent 参与的网站、工具、agent、内容系统或 demo。
- 你希望后续 session 先读取稳定项目状态，而不是重新解释所有背景。
- 你希望项目里有一个轻量的 project brain，记录“为什么这样做”和“下一步是什么”。
- 你经常在 Codex、Claude Code、Cursor、Kimi Code、Trae、Deepseek 或其他工具之间切换。
- 你希望把重要决策、风险、TODO 和来源证据留在 repo 里。
- 你希望项目上下文是 plain files，可以被人类阅读、审查和手动修改。
- 你希望新 agent 先理解项目边界，再开始修改文件。

### 常见信号

- 你经常在新 session 里重新解释项目背景。
- agent 忘了之前已经接受的决策。
- agent 修改方向越来越偏离最初目标。
- session reset 或 context compact 后，下一步行动丢失。
- 你不确定哪些结论来自事实，哪些只是聊天中的猜测。

### 不适合的场景

- 你需要完整的项目管理系统，而不是轻量 context layer。
- 你需要自动记住所有聊天、文件和行为的长期 memory database。
- 你需要多人权限、审批流、通知、甘特图、看板或团队报表。
- 你需要直接连接飞书、钉钉、Notion、Jira、Slack 或内部系统。
- 你需要生成 slides、HTML brief、周报、图表或可视化报告。
- 你希望工具自动改写宿主 agent instruction files。

### 典型使用时机

在新项目第一天：

```txt
先建立 project-context/，再让 agent 开始实现功能。
```

在新 session 开始时：

```txt
先读取 project-context/README.md 及其列出的上下文文件，再总结当前目标、边界、决策、风险和下一步。
```

在一次重要修改完成后：

```txt
把稳定状态写回 PROJECT_CONTEXT.md、AGENT_BRIEF.md、DECISIONS.md、RISKS.md 和 TODO.md。
```

### 和其他工具的关系

Agent Project Context Layer 可以和任何能读取 workspace Markdown files 的 coding agent 一起使用。

它不替代 coding agent。它给 coding agent 一个更稳定的项目上下文入口。

它不替代 project management app。它只维护项目上下文中最容易漂移的部分。

它不替代 memory database。它刻意采用可见、可审查、可手动编辑的 plain files。

## English

Agent Project Context Layer is useful when starting a new project that needs durable project context over time.

The core issue is not "sharing one file across many agents." The issue is that repeated discussions with coding agents can make goals, boundaries, decisions, risks, and next actions drift.

### Good Fits

- You are starting a website, tool, agent, content system, or demo with a coding agent.
- You want future sessions to read stable project state instead of re-explaining all context.
- You want a lightweight project brain that records why choices were made and what should happen next.
- You switch between Codex, Claude Code, Cursor, Kimi Code, Trae, Deepseek, or other tools.
- You want important decisions, risks, TODOs, and source evidence to live in the repo.
- You want project context to be plain files that humans can read, review, and edit.
- You want a new agent to understand project boundaries before editing files.

### Common Signals

- You often re-explain the project background in a new session.
- The agent forgets decisions that were already accepted.
- The agent drifts away from the original direction.
- The next action gets lost after a session reset or context compact.
- You are unsure which claims came from evidence and which were only chat guesses.

### Poor Fits

- You need a complete project management system, not a lightweight context layer.
- You need a long-term memory database that automatically records every chat, file, and action.
- You need multi-user permissions, approvals, notifications, Gantt charts, boards, or team reports.
- You need direct connections to Feishu, DingTalk, Notion, Jira, Slack, or internal systems.
- You need slides, HTML briefs, weekly reports, charts, or visual reports.
- You expect the tool to automatically rewrite host-agent instruction files.

### Typical Moments

On day one of a new project:

```txt
Set up project-context/ before asking the agent to implement features.
```

At the start of a new session:

```txt
Read project-context/README.md and the context files it lists, then summarize current goals, boundaries, decisions, risks, and next action.
```

After meaningful work:

```txt
Write durable state back to PROJECT_CONTEXT.md, AGENT_BRIEF.md, DECISIONS.md, RISKS.md, and TODO.md.
```

### Relationship To Other Tools

Agent Project Context Layer works with any coding agent that can read workspace Markdown files.

It does not replace the coding agent. It gives the coding agent a more stable project context entry point.

It does not replace a project management app. It maintains the parts of project context that drift most easily.

It does not replace a memory database. It intentionally uses visible, inspectable, manually editable plain files.
