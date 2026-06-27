# 3 分钟安装和使用 / Install And Use In 3 Minutes

## 中文

这个 package 对应 `agent-project-context-layer` v0.1.0。

默认安装是非侵入式的：只创建 `project-context/`，不修改任何 agent instruction file。

推荐路径：先安装 Skill，再把 setup prompt 发给你当前正在用的 coding agent，让它在目标项目里创建或更新 `project-context/`。

### 方式 A：一行命令安装 Skill（推荐）

```sh
npx skills add https://github.com/ForestFlow3/agent-project-context-layer --skill agent-project-context-layer
```

然后打开目标项目，把方式 B 的 setup prompt 发给 coding agent。

### 方式 B：把这段话直接发给 AI

```txt
请为本项目建立 Agent Project Context Layer。

在 project-context/ 下创建或更新 README.md、PROJECT_CONTEXT.md、AGENT_BRIEF.md、DECISIONS.md、RISKS.md、TODO.md。

这些文件是普通项目数据。不要创建或修改 AGENTS.md、AGENT.md、CLAUDE.md、.cursor/rules/ 或其他 agent instruction files。

只根据我明确提供的材料填写内容。已有文件需要合并，不要覆盖决策历史、风险历史或用户内容。

不要编造事实。缺失信息先问我，或记录为未决问题。
```

### 方式 C：手动命令行

```sh
mkdir -p project-context
for f in README.md PROJECT_CONTEXT.md AGENT_BRIEF.md DECISIONS.md RISKS.md TODO.md; do [ -e "project-context/$f" ] || cp "path/to/agent-project-context-layer/starters/project-context/$f" "project-context/$f"; done
```

安装结果：

```txt
project-context/
  README.md
  PROJECT_CONTEXT.md
  AGENT_BRIEF.md
  DECISIONS.md
  RISKS.md
  TODO.md
```

### 开始工作

```txt
读取 project-context/README.md 及其列出的上下文文件。

修改前总结当前目标、边界、决策、风险、未决问题和下一步行动。
```

### 新 Session / Reset 前

新 session 开始时：

```txt
先读取 project-context/README.md 及其列出的上下文文件，再开始规划或修改。
```

结束、重置或压缩 session 前：

```txt
把本次已经稳定下来的目标变化、决策、风险、TODO、未决问题和来源证据写回 project-context/。
不要写入临时推理或未确认猜测。
```

### 更新规则

```txt
基于本次变化更新 project-context/ 下的 Agent Project Context Layer。

只记录稳定项目状态、已接受决策、已知风险、未决问题、来源证据和下一步行动。

不要编造事实，也不要重写历史。
```

### 可选：显式接入宿主

需要每次 session 自动发现时，先让 AI 展示目标 instruction file 和完整 patch。只有你明确批准后，才写入带 `BEGIN/END` 标记且可独立删除的区块。

## English

This package is for `agent-project-context-layer` v0.1.0.

Default setup is non-invasive: it creates only `project-context/` and does not modify any agent instruction file.

Recommended path: install the Skill, then send the setup prompt to the coding agent you are using inside the target project.

### Option A: Install The Skill With One Command (Recommended)

```sh
npx skills add https://github.com/ForestFlow3/agent-project-context-layer --skill agent-project-context-layer
```

Then open the target project and send the Option B setup prompt to your coding agent.

### Option B: Paste This To AI

```txt
Set up Agent Project Context Layer for this project.

Create or update README.md, PROJECT_CONTEXT.md, AGENT_BRIEF.md, DECISIONS.md, RISKS.md, and TODO.md under project-context/.

These files are ordinary project data. Do not create or modify AGENTS.md, AGENT.md, CLAUDE.md, .cursor/rules/, or any other agent instruction file.

Use only materials I explicitly provide. Merge existing files without overwriting decision history, risk history, or user content.

Do not invent facts. Ask me for missing context or record it as an open question.
```

### Option C: Manual Command Line

```sh
mkdir -p project-context
for f in README.md PROJECT_CONTEXT.md AGENT_BRIEF.md DECISIONS.md RISKS.md TODO.md; do [ -e "project-context/$f" ] || cp "path/to/agent-project-context-layer/starters/project-context/$f" "project-context/$f"; done
```

Installed files:

```txt
project-context/
  README.md
  PROJECT_CONTEXT.md
  AGENT_BRIEF.md
  DECISIONS.md
  RISKS.md
  TODO.md
```

### Start Work

```txt
Read project-context/README.md and the context files it lists.

Before editing, summarize the current goal, boundaries, decisions, risks, open questions, and next action.
```

### New Session / Before Reset

At the start of a new session:

```txt
Read project-context/README.md and the context files it lists before planning or editing.
```

Before ending, resetting, or compacting a session:

```txt
Write durable goal changes, decisions, risks, TODOs, open questions, and source evidence back to project-context/.
Do not record temporary reasoning or unconfirmed guesses.
```

### Update Rule

```txt
Update the Agent Project Context Layer under project-context/ based on this change.

Record only durable project state, accepted decisions, known risks, open questions, source evidence, and next actions.

Do not invent facts or rewrite history.
```

### Optional: Explicit Host Integration

For automatic discovery in every session, first ask the AI to show the target instruction file and exact patch. Write only after explicit approval, using a removable block with `BEGIN/END` markers.
