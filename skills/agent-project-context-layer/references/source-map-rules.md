# Source Map 规则 / Source Map Rules

## 中文

每个重要项目结论都应该可追溯。

### Source ID 格式

使用短 ID：

```txt
S001
S002
S003
```

### 什么需要来源

- 项目目标。
- 已接受决策。
- 用户约束。
- 截止日期。
- 负责人。
- 风险。
- 范围边界。
- 外部结论。

### 置信度

- `high`：明确用户陈述、直接本地来源或稳定 source file。
- `medium`：从多个 notes 中推断得出。
- `low`：线索较弱、来源不完整或需要验证。

### 规则

如果 agent 无法引用来源，应把该项标记为 open question，而不是作为事实呈现。

## English

Every important project claim should be traceable.

### Source ID Format

Use short IDs:

```txt
S001
S002
S003
```

### What Needs A Source

- Project goal.
- Accepted decisions.
- User constraints.
- Deadlines.
- Owners.
- Risks.
- Scope boundaries.
- External claims.

### Confidence

- `high`: explicit user statement, direct local source, or stable source file.
- `medium`: inferred from multiple notes.
- `low`: weak clue, incomplete source, or needs verification.

### Rule

If the agent cannot cite a source, it should mark the item as an open question instead of presenting it as fact.
