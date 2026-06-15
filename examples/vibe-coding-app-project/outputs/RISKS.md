# RISKS

## 中文

| ID | 风险 | 严重性 | 缓解方式 | 来源 |
|---|---|---|---|---|
| R001 | 字段太多可能让捕捉想法变慢。 | medium | 将 v0.1 字段限制为 title、raw note、tags、target format、status 和 last touched date。 | S003 |
| R002 | AI outline generation 可能编造 raw note 中不存在的细节。 | medium | 将 outline output 标记为 placeholder，并要求它基于选中的 idea。 | S003 |
| R003 | 如果浏览器数据被清除，local storage data 可能丢失。 | low | 在 v0.1 中记录这个限制，并后置 export/import 决策。 | S003 |

风险规则：如果实现压力推动项目走向 backend、sync、login 或 AI generation，停止并请求范围确认。

## English

| ID | Risk | Severity | Mitigation | Sources |
|---|---|---|---|---|
| R001 | Too many fields may make idea capture slow. | medium | Keep v0.1 fields limited to title, raw note, tags, target format, status, and last touched date. | S003 |
| R002 | AI outline generation may invent details not present in the raw note. | medium | Mark outline output as a placeholder and require it to stay grounded in the selected idea. | S003 |
| R003 | Local storage data can be lost if browser data is cleared. | low | Document this limitation in v0.1 and defer export/import decisions. | S003 |

Risk rule: if implementation pressure pushes toward backend, sync, login, or AI generation, stop and ask for scope confirmation.
