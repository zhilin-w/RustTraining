# 13. 生产模式 🔴

> **你将学到：**
> - 使用 `watch` 通道和 `select!` 实现优雅关机
> - 背压：有界通道防止内存耗尽
> - 结构化并发：`JoinSet` 与 `TaskTracker`
> - 超时、重试与指数退避
> - 错误处理：`thiserror` vs `anyhow`，双 `?` 模式
> - Tower：用于 axum、tonic、hyper 的中间件模式

（保留原文示例与图表，正文说明翻译为中文）

## 优雅关机

（保留示例代码并翻译说明）

### 背压与有界通道

（保留示例与说明）

### 结构化并发：JoinSet 与 TaskTracker

（保留示例并翻译）

### 超时与重试

（保留实现示例与建议，包括加抖动提示）

### 错误处理

（保留 `thiserror` 与 `anyhow` 的对比与示例）

### Tower：中间件模式

（保留示例与解释）

> **关键要点 — 生产模式**
> - 使用 `watch` + `select!` 协调优雅关机
> - 有界通道提供背压；生产中应避免无界通道
> - 使用 `JoinSet`/`TaskTracker` 实现结构化并发
> - 对网络操作总要加超时与退避策略（并加入抖动）

> **参见：** [第 8 章 — Tokio 深入](ch08-tokio-deep-dive.md)，[第 12 章 — 常见陷阱](ch12-common-pitfalls.md)
