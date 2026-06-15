# PROJECT_CONTEXT

## 中文

这个文件是项目的稳定上下文锚点。

### 项目目标

用一段话写清项目目标。

### 当前阶段

使用以下值之一：

- 想法
- 原型
- demo
- 发布
- 迭代
- 暂停

### 目标用户

- 

### 项目边界

- agent 可以修改什么：
- 没有批准时 agent 不能修改什么：
- 私人或敏感材料：

### 非目标

- 

### 当前状态

- 

### 重要文件

| 文件 | 用途 |
|---|---|
| `README.md` | Context Layer 文件清单和非侵入式使用边界。 |
| `AGENT_BRIEF.md` | 给新 agent session 的快速交接 brief。 |
| `DECISIONS.md` | 已接受决策。 |
| `RISKS.md` | 已知风险和缓解方式。 |
| `TODO.md` | 当前下一步行动。 |

### 未决问题

| ID | 问题 | 负责人 | 状态 | 来源 |
|---|---|---|---|---|
| Q001 |  | human | open |  |

### 来源映射

| 来源 ID | 路径或 URL | 支持什么结论 | 置信度 |
|---|---|---|---|
| S001 |  |  | medium |

### Agent 规则

- 编辑前读取 `AGENT_BRIEF.md`。
- 改变项目方向前，检查决策、风险、TODO、未决问题和 source map。
- 不要编造需求、用户、指标或日期。
- 当稳定项目状态变化时，更新这个 layer。

## English

This file is the stable context anchor for the project.

### Project Goal

Write the project goal in one paragraph.

### Current Stage

Use one of these values:

- idea
- prototype
- demo
- release
- iteration
- paused

### Target Users

- 

### Project Boundaries

- What the agent may change:
- What the agent must not change without approval:
- Private or sensitive materials:

### Non-Goals

- 

### Current State

- 

### Important Files

| File | Purpose |
|---|---|
| `README.md` | Context Layer manifest and non-invasive usage boundary. |
| `AGENT_BRIEF.md` | Fast handoff brief for new agent sessions. |
| `DECISIONS.md` | Accepted decisions. |
| `RISKS.md` | Known risks and mitigations. |
| `TODO.md` | Current next actions. |

### Open Questions

| ID | Question | Owner | Status | Sources |
|---|---|---|---|---|
| Q001 |  | human | open |  |

### Source Map

| Source ID | Path Or URL | What It Supports | Confidence |
|---|---|---|---|
| S001 |  |  | medium |

### Agent Rules

- Read `AGENT_BRIEF.md` before editing.
- Check decisions, risks, TODOs, open questions, and source map before changing project direction.
- Do not invent requirements, users, metrics, or dates.
- Update this layer when durable project state changes.
