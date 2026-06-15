# DECISIONS

## 中文

| ID | 日期 | 决策 | 理由 | 状态 | 来源 |
|---|---|---|---|---|---|
| D001 | 2026-06-09 | 把 v0.1 构建为不带 backend 的 static local web app。 | 让第一个 demo 保持小，并且容易被 coding agents 修改。 | accepted | S002 |
| D002 | 2026-06-09 | demo data 只使用 local browser storage。 | 在不引入 account systems 或 external services 的情况下支持 local-first 行为。 | accepted | S002 |
| D003 | 2026-06-09 | v0.1 中把 AI outline generation 保持为 placeholder。 | 在 capture workflow 被验证前，避免漂移成完整 AI writing app。 | accepted | S002, S003 |

决策规则：除非用户明确改变项目范围，否则不要添加 backend、login、external APIs、analytics 或 account systems。

## English

| ID | Date | Decision | Reason | Status | Sources |
|---|---|---|---|---|---|
| D001 | 2026-06-09 | Build v0.1 as a static local web app with no backend. | Keeps the first demo small and easy for coding agents to modify. | accepted | S002 |
| D002 | 2026-06-09 | Use local browser storage only for demo data. | Supports local-first behavior without account systems or external services. | accepted | S002 |
| D003 | 2026-06-09 | Keep AI outline generation as a placeholder in v0.1. | Avoids drifting into a full AI writing app before the capture workflow is validated. | accepted | S002, S003 |

Decision rule: do not add backend, login, external APIs, analytics, or account systems unless the user explicitly changes project scope.
