# PROJECT_CONTEXT

## 中文

这是一个 synthetic 示例输出。

### 项目目标

构建 `Spark Shelf`，一个小型 local-first 灵感收集箱，帮助独立创作者捕捉原始想法、添加 tags，并把选中的 notes 变成短大纲。

来源：S001。

### 当前阶段

原型规划阶段。

来源：S002、S003。

### 目标用户

- 独立创作者。
- vibe coding 用户。
- 使用 coding agents 的知识工作者。

来源：S001。

### 项目边界

- v0.1 应该是一个静态 local web app。
- 不做 backend。
- 不做 login。
- 不接 external API。
- 不做 analytics。
- 不做 social platform、sync service 或 cloud account system。
- v0.1 不做完整 AI writing app。

来源：S001、S002。

### 当前状态

项目想法、范围边界、第一个 demo 形态、可能的数据字段、状态值、风险和下一步行动都来自 synthetic notes。

目前还没有实现。

来源：S001、S002、S003。

### 核心数据字段

- 想法标题。
- 原始 note。
- tags。
- 目标格式。
- 状态。
- 最近触达日期。

来源：S003。

### 状态值

- 原始
- 已成形
- 已起草
- 已发布

来源：S003。

### 第一个 Demo 应展示

1. 想法列表。
2. tag 过滤。
3. 选中想法详情。
4. 生成大纲占位。

来源：S002。

### 未决问题

| ID | 问题 | 负责人 | 状态 | 来源 |
|---|---|---|---|---|
| Q001 | 第一个 demo 应该是单个 HTML 文件，还是带独立 assets 的小型 static app？ | human | open | S002 |
| Q002 | 当 local browser storage 被清除时应该发生什么？ | human | open | S003 |
| Q003 | export/import 应该放进 v0.1，还是后置？ | human | open | S003 |

### 来源映射

| 来源 ID | 路径 | 支持什么结论 | 置信度 |
|---|---|---|---|
| S001 | `inputs/idea-note.md` | 项目想法、用户问题、初始功能列表和范围边界。 | high |
| S002 | `inputs/session-note-01.md` | 静态 local app 决策、第一个 demo UI 范围、偏好技术形态和 AI writing app 担心点。 | high |
| S003 | `inputs/feature-notes.md` | 数据字段、状态值、风险和下一步行动。 | high |

### Agent 规则

- 编辑前读取 `AGENT_BRIEF.md`。
- 没有明确批准，不要添加 backend、login、analytics、external APIs 或 account systems。
- 让 AI outline 行为始终基于原始想法。
- 在项目发生有意义变化后更新这个 context layer。

## English

This is a synthetic example output.

### Project Goal

Build `Spark Shelf`, a tiny local-first inspiration inbox that helps a solo creator capture raw ideas, tag them, and shape selected notes into short outlines.

Sources: S001.

### Current Stage

Prototype planning.

Sources: S002, S003.

### Target Users

- Solo creator.
- Vibe coding user.
- Knowledge worker using coding agents.

Sources: S001.

### Project Boundaries

- v0.1 should be a static local web app.
- No backend.
- No login.
- No external API.
- No analytics.
- No social platform, sync service, or cloud account system.
- No full AI writing app in v0.1.

Sources: S001, S002.

### Current State

The project idea, scope boundary, first demo shape, potential data fields, status values, risks, and next actions are defined from synthetic notes.

No implementation exists yet.

Sources: S001, S002, S003.

### Core Data Fields

- Idea title.
- Raw note.
- Tags.
- Target format.
- Status.
- Last touched date.

Sources: S003.

### Status Values

- raw
- shaped
- drafted
- shipped

Sources: S003.

### First Demo Should Show

1. Idea list.
2. Tag filter.
3. Selected idea detail.
4. Generated outline placeholder.

Sources: S002.

### Open Questions

| ID | Question | Owner | Status | Sources |
|---|---|---|---|---|
| Q001 | Should the first demo be one HTML file or a small static app with separate assets? | human | open | S002 |
| Q002 | What should happen when local browser storage is cleared? | human | open | S003 |
| Q003 | Should export/import be in v0.1 or deferred? | human | open | S003 |

### Source Map

| Source ID | Path | What It Supports | Confidence |
|---|---|---|---|
| S001 | `inputs/idea-note.md` | Project idea, user problem, initial feature list, and scope boundary. | high |
| S002 | `inputs/session-note-01.md` | Static local app decision, first demo UI scope, preferred stack, and AI writing app concern. | high |
| S003 | `inputs/feature-notes.md` | Data fields, status values, risks, and next actions. | high |

### Agent Rules

- Read `AGENT_BRIEF.md` before editing.
- Do not add backend, login, analytics, external APIs, or account systems without explicit approval.
- Keep AI outline behavior grounded in the raw idea.
- Update this context layer after meaningful project changes.
