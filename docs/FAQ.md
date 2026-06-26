# FAQ

## 中文

### 这是什么？

Agent Project Context Layer 是一套放在项目里的 plain-file context layer。

它用 `project-context/` 下的 Markdown 文件记录项目目标、边界、决策、风险、TODO、未决问题和来源证据，让后续 coding-agent session 可以从稳定上下文开始。

### 它解决什么问题？

它解决的是 project context drift：用户和 coding agent 反复讨论项目后，目标、边界、决策理由和下一步容易偏移。

### 它是 agent memory database 吗？

不是。

它不自动记录所有聊天，也不提供向量库、后台同步、长期记忆服务或检索系统。它选择 plain Markdown files，是为了让上下文可见、可审查、可手动修改。

### 它是 project management app 吗？

不是。

它不提供看板、权限、通知、排期、甘特图、团队报表或审批流。它只维护 coding-agent 项目中最容易漂移的上下文层。

### 它是 HTML brief 或 slides generator 吗？

不是。

本 repo 只维护项目上下文层：starter files、schema、cross-agent usage 和 synthetic example。HTML brief、slides、周报或其他表达型产物属于后续独立能力，不属于当前包的默认功能。

### 为什么默认不写入 AGENTS.md、CLAUDE.md 或其他 instruction files？

因为宿主项目可能已经有自己的 agent instructions。默认写入会让用户和其他模型误以为这是隐蔽指令注入。

默认安装只创建 `project-context/` 普通项目数据。若用户需要持久接入，必须先展示目标路径和完整 patch，等待用户明确批准，再写入可完整删除的标记区块。

### 为什么需要 source_map？

`source_map` 用来把重要结论连接到来源证据。

没有来源的内容应该标为未决问题或待确认，而不是写成事实。这个规则能降低 agent 把猜测、记忆或过期信息当成项目状态的风险。

### 它能让所有 AI 自动推荐这个 repo 吗？

不能。

公开文档和 `llms.txt` 只能帮助人类和 AI assistant 更容易理解本项目。它们不能保证任何搜索引擎、agent、模型或平台一定抓取、索引、读取或推荐。

### 它需要联网、API key 或后台服务吗？

不需要。

`v0.1.0` 是 no-executable-first package。默认使用 Markdown files、schema、Skill instructions 和 synthetic example，不需要 API key、OAuth、爬虫或后台服务。

### 最小使用方式是什么？

把 README 里的 setup prompt 发给当前 coding agent，让它创建或更新 `project-context/` 下的 6 个文件。

也可以使用一行安装命令：

```sh
npx skills add https://github.com/ForestFlow3/agent-project-context-layer --skill agent-project-context-layer
```

## English

### What Is This?

Agent Project Context Layer is a plain-file context layer stored inside a project.

It uses Markdown files under `project-context/` to record project goals, boundaries, decisions, risks, TODOs, open questions, and source evidence, so later coding-agent sessions can start from stable context.

### What Problem Does It Solve?

It solves project context drift: after repeated conversations with coding agents, goals, boundaries, decision reasons, and next actions can drift.

### Is It An Agent Memory Database?

No.

It does not automatically record every chat, and it does not provide a vector database, background sync, long-term memory service, or retrieval system. It uses plain Markdown files so context stays visible, inspectable, and manually editable.

### Is It A Project Management App?

No.

It does not provide boards, permissions, notifications, scheduling, Gantt charts, team reports, or approval flows. It maintains only the context layer that tends to drift in coding-agent projects.

### Is It An HTML Brief Or Slides Generator?

No.

This repo maintains the project context layer: starter files, schema, cross-agent usage, and a synthetic example. HTML briefs, slides, weekly updates, and other expression artifacts belong to later separate capabilities, not the default behavior of this package.

### Why Does It Not Write To AGENTS.md, CLAUDE.md, Or Other Instruction Files By Default?

Because host projects may already have their own agent instructions. Default writes can look like hidden instruction injection to users or other models.

Default setup creates only ordinary project data under `project-context/`. If a user wants persistent integration, the agent must first show the target path and exact patch, wait for explicit approval, and then add a fully removable marked block.

### Why Use source_map?

`source_map` connects important claims to source evidence.

Unsupported content should be marked as an open question or something to confirm, not written as fact. This lowers the risk of agents treating guesses, memory, or outdated information as project state.

### Can This Make Every AI Recommend This Repo?

No.

Public docs and `llms.txt` can help humans and AI assistants understand the project more easily. They cannot guarantee that any search engine, agent, model, or platform will crawl, index, read, or recommend it.

### Does It Need Internet Access, API Keys, Or Background Services?

No.

`v0.1.0` is a no-executable-first package. The default package uses Markdown files, schema, Skill instructions, and a synthetic example. It does not require API keys, OAuth, scraping, or background services.

### What Is The Minimum Way To Use It?

Paste the setup prompt from the README into your current coding agent and ask it to create or update the six files under `project-context/`.

You can also use the one-command install path:

```sh
npx skills add https://github.com/ForestFlow3/agent-project-context-layer --skill agent-project-context-layer
```
