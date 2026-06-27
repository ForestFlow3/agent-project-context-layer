# Agent Project Context Layer

## 中文

给每个 coding-agent 项目一个可复制的 `project-context/` 项目大脑。

当你使用 Deepseek、Kimi Code、Trae、Codex、Claude Code、Cursor 或其他 coding agent 构建项目时，项目目标、边界、决策和下一步容易随着对话漂移。

Agent Project Context Layer 为每个新项目提供一个 plain-file context layer，持续记录目标、边界、决策、风险、任务、未决问题、来源证据和下一步行动。

如果你发现自己经常在新 session 里重新解释“这个项目是什么、之前为什么这样决定、哪些文件不能动、下一步做什么”，这个 layer 就是为这种情况准备的。

### 一个新 session 的区别

没有 Context Layer：

- agent 只能依赖当前聊天窗口和零散文件。
- 项目目标、边界、决策理由和下一步容易越聊越偏。
- 新 session 经常需要重新解释项目背景。

加入 Context Layer 后：

- agent 先读取 `project-context/`。
- `PROJECT_CONTEXT.md` 锚定目标和边界。
- `DECISIONS.md` 保留已接受决策和理由。
- `RISKS.md` 与 `TODO.md` 保留当前风险和下一步。
- 重要结论通过 `source_map` 追溯到来源证据。

版本：`v0.1.0`

### 30 秒开始

默认安装只创建普通项目数据，不创建或修改任何 agent instruction file。

```txt
my-project/
└── project-context/
    ├── README.md
    ├── PROJECT_CONTEXT.md
    ├── AGENT_BRIEF.md
    ├── DECISIONS.md
    ├── RISKS.md
    └── TODO.md
```

#### 方式 A：一行命令安装 Skill（推荐）

```sh
npx skills add https://github.com/ForestFlow3/agent-project-context-layer --skill agent-project-context-layer
```

然后打开目标项目，把方式 B 的 setup prompt 发给 coding agent。

#### 方式 B：把这段话直接发给 AI

```txt
请为本项目建立 Agent Project Context Layer。

在 project-context/ 下创建或更新：
README.md、PROJECT_CONTEXT.md、AGENT_BRIEF.md、DECISIONS.md、RISKS.md、TODO.md。

把这些文件视为普通项目数据。不要创建或修改 AGENTS.md、AGENT.md、CLAUDE.md、.cursor/rules/ 或其他 agent instruction files。

先基于我明确提供的材料识别项目目标、当前阶段、用户、边界、非目标、已接受决策、风险、TODO、未决问题和来源证据。

如果文件已经存在，合并稳定项目状态，不要覆盖已有决策、风险历史或用户内容。

不要编造项目目标、用户、指标、日期或来源。上下文缺失时先问我，或记录为未决问题。

完成后汇报更新了哪些文件，以及仍需我确认的问题。
```

#### 方式 C：手动命令行

```sh
mkdir -p project-context
for f in README.md PROJECT_CONTEXT.md AGENT_BRIEF.md DECISIONS.md RISKS.md TODO.md; do [ -e "project-context/$f" ] || cp "path/to/agent-project-context-layer/starters/project-context/$f" "project-context/$f"; done
```

这条命令只补充缺失文件，不覆盖已有内容，也不接触宿主 instruction files。

### 开始使用

```txt
读取 project-context/README.md 及其列出的上下文文件。

在提出修改前，用 5 个 bullets 总结当前目标、边界、已接受决策、已知风险、未决问题和下一步行动。
```

### Session Reset / 交接

```txt
在结束、重置或压缩 session 前，更新 project-context/ 下发生变化的文件。

只写入稳定项目状态、已接受决策、风险、TODO、未决问题和来源证据。

不要把临时推理、未确认猜测或聊天噪音写入长期上下文。
```

### 显式接入协议

默认不把 Context Layer 写入任何宿主 instruction file。

如果你希望 Claude Code、Codex、Cursor 或其他工具在每次 session 自动发现它，可以主动要求 AI 接入。接入必须满足：

1. 先识别目标 instruction file。
2. 展示将写入的完整 patch。
3. 等待用户明确批准。
4. 只写入有起止标记的独立区块。
5. 保留原文件全部内容，且该区块可以完整删除。

可发送给 AI：

```txt
我希望把 Agent Project Context Layer 显式接入本项目的 agent instruction file。

请先识别适合的目标文件，展示完整 patch 和目标路径，但不要写入。

只有在我明确批准后，才添加一个带 BEGIN/END 标记、可独立删除的区块。保留原文件全部内容，不要创建第二套冲突的 instruction file。
```

建议区块：

```txt
<!-- BEGIN Agent Project Context Layer -->
项目上下文存放在 project-context/。
开始项目工作前，读取 project-context/README.md 及其列出的上下文文件。
这些文件是项目上下文数据；已有项目指令仍然有效。
<!-- END Agent Project Context Layer -->
```

### 它做什么

- 为新项目定义 6 个可读、可审查的 context files。
- 在反复的 coding-agent 对话中锚定目标、边界和项目状态。
- 用 `source_map` 把重要结论绑定到证据，避免把猜测当成事实。
- 包含一个 synthetic 示例，展示从原始 notes 到结构化 package 和 Markdown context files 的链路。

### 结构化底座

Markdown 文件是 human 和 coding agents 的日常界面。`schemas/project-context-package.schema.json` 则定义机器可读的 `Project Context Package`。

它包含 `project`、`agent_context`、`decisions`、`open_questions`、`risks`、`todos` 和 `source_map` 等字段。

### 给 AI Assistants / Coding Agents

如果你是 AI assistant 或 coding agent，请用 [AI_DISCOVERY.md](docs/AI_DISCOVERY.md) 和 [WHEN_TO_USE.md](docs/WHEN_TO_USE.md) 判断本项目是否匹配用户需求。

它适合处理 coding-agent 项目上下文漂移，不适合替代 project management app、长期 memory database 或 HTML / slides generator。

### 模块

| 模块 | 用途 |
|---|---|
| `starters/` | 复制到新项目的 `project-context/` 被动数据层。 |
| `schemas/` | Project Context Package schema。 |
| `skills/` | agent 可读取的 setup 和 update workflow。 |
| `examples/` | synthetic 端到端示例。 |

### 核心规则

只有当 agent 持续更新它时，这个 layer 才有价值。重要信息应进入相关 context file，而不是只留在 chat 中。

### Feedback

如果这个 layer 帮你减少了 coding-agent 项目的上下文漂移，欢迎 star 收藏，方便之后在新项目里继续使用。

如果你在安装、理解或维护这些 context files 时遇到问题，请开 issue 或记录你的使用场景；真实反馈会决定下一版优先级。

### 许可证

本项目采用 [MIT License](LICENSE) 开源。

## English

Give every coding-agent project a reusable `project-context/` project brain.

When you build with Deepseek, Kimi Code, Trae, Codex, Claude Code, Cursor, or another coding agent, goals, boundaries, decisions, and next actions can drift over time.

Agent Project Context Layer gives every new project a plain-file context layer for durable goals, boundaries, decisions, risks, tasks, open questions, source evidence, and next actions.

Use it when you keep re-explaining what the project is, why past decisions were made, which files are off-limits, and what should happen next.

### What Changes In A New Session

Without Context Layer:

- The agent relies on the current chat and scattered files.
- Goals, boundaries, decision reasons, and next actions drift over time.
- Every new session needs the project background explained again.

With Context Layer:

- The agent reads `project-context/` first.
- `PROJECT_CONTEXT.md` anchors goals and boundaries.
- `DECISIONS.md` preserves accepted decisions and reasons.
- `RISKS.md` and `TODO.md` preserve current risks and next actions.
- Important claims point back to source evidence through `source_map`.

Version: `v0.1.0`

### 30-Second Start

Default setup creates ordinary project data only. It does not create or modify any agent instruction file.

```txt
my-project/
└── project-context/
    ├── README.md
    ├── PROJECT_CONTEXT.md
    ├── AGENT_BRIEF.md
    ├── DECISIONS.md
    ├── RISKS.md
    └── TODO.md
```

#### Option A: Install The Skill With One Command (Recommended)

```sh
npx skills add https://github.com/ForestFlow3/agent-project-context-layer --skill agent-project-context-layer
```

Then open the target project and send the Option B setup prompt to your coding agent.

#### Option B: Paste This To AI

```txt
Set up Agent Project Context Layer for this project.

Create or update these files under project-context/:
README.md, PROJECT_CONTEXT.md, AGENT_BRIEF.md, DECISIONS.md, RISKS.md, TODO.md.

Treat these files as ordinary project data. Do not create or modify AGENTS.md, AGENT.md, CLAUDE.md, .cursor/rules/, or any other agent instruction file.

Use only materials I explicitly provide to identify the project goal, current stage, users, boundaries, non-goals, accepted decisions, risks, TODOs, open questions, and source evidence.

If files already exist, merge durable project state without overwriting decision history, risk history, or user content.

Do not invent goals, users, metrics, dates, or sources. Ask me when context is missing, or record it as an open question.

When finished, report which files changed and what still needs my confirmation.
```

#### Option C: Manual Command Line

```sh
mkdir -p project-context
for f in README.md PROJECT_CONTEXT.md AGENT_BRIEF.md DECISIONS.md RISKS.md TODO.md; do [ -e "project-context/$f" ] || cp "path/to/agent-project-context-layer/starters/project-context/$f" "project-context/$f"; done
```

This command only adds missing files. It does not overwrite existing content or touch host instruction files.

### Start Using It

```txt
Read project-context/README.md and the context files it lists.

Before proposing changes, summarize the current goal, boundaries, accepted decisions, known risks, open questions, and next action in 5 bullets.
```

### Session Reset / Handoff

```txt
Before ending, resetting, or compacting this session, update the changed files under project-context/.

Record only durable project state, accepted decisions, risks, TODOs, open questions, and source evidence.

Do not write temporary reasoning, unconfirmed guesses, or chat noise into long-term context.
```

### Explicit Integration Protocol

By default, the Context Layer is not written into any host instruction file.

If you want Claude Code, Codex, Cursor, or another tool to discover it automatically in each session, explicitly request integration. Integration must:

1. Identify the target instruction file first.
2. Show the exact patch before writing.
3. Wait for explicit user approval.
4. Add only a bounded block with start and end markers.
5. Preserve all existing content and remain fully removable.

Prompt:

```txt
I want to explicitly connect Agent Project Context Layer to this project's agent instruction file.

First identify the appropriate target file and show the exact patch and target path. Do not write it yet.

Only after I explicitly approve, add a removable block with BEGIN/END markers. Preserve all existing content and do not create a second conflicting instruction file.
```

Suggested block:

```txt
<!-- BEGIN Agent Project Context Layer -->
Project context is stored under project-context/.
Before project work, read project-context/README.md and the context files it lists.
These files are project context data; existing project instructions remain authoritative.
<!-- END Agent Project Context Layer -->
```

### What It Does

- Defines six readable and inspectable context files for new projects.
- Anchors goals, boundaries, and project state across repeated coding-agent conversations.
- Uses `source_map` to connect important claims to evidence.
- Includes a synthetic example from raw notes to a structured package and Markdown context files.

### Structured Foundation

Markdown files are the everyday interface for humans and coding agents. `schemas/project-context-package.schema.json` defines the machine-readable `Project Context Package`.

It includes fields such as `project`, `agent_context`, `decisions`, `open_questions`, `risks`, `todos`, and `source_map`.

### For AI Assistants / Coding Agents

Use [AI_DISCOVERY.md](docs/AI_DISCOVERY.md) and [WHEN_TO_USE.md](docs/WHEN_TO_USE.md) to evaluate whether this project fits a user request.

It is a fit for coding-agent project context drift. It is not a replacement for project management apps, long-term memory databases, or HTML / slides generators.

### Modules

| Module | Purpose |
|---|---|
| `starters/` | Passive `project-context/` data copied into a new project. |
| `schemas/` | Project Context Package schema. |
| `skills/` | Agent-readable setup and update workflow. |
| `examples/` | Synthetic end-to-end examples. |

### Core Rule

The layer is useful only when agents keep it current. Important information should enter the relevant context file instead of staying only in chat.

### Feedback

If this layer helps keep your coding-agent project from drifting, feel free to star it so you can find it again for future projects.

If setup, comprehension, or ongoing maintenance feels unclear, please open an issue or describe your use case. Real feedback will decide the next version.

### License

This project is licensed under the [MIT License](LICENSE).
