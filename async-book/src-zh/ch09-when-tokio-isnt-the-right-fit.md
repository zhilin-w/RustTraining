# 9. 当 Tokio 不适合时 🟡

> **你将学到：**
> - `'static` 问题：`tokio::spawn` 会让你到处使用 `Arc`
> - `LocalSet` 支持 `!Send` futures
> - `FuturesUnordered` 适合借用友好的并发（无需 spawn）
> - `JoinSet` 用于托管任务组
> - 编写运行时无关的库

（保留原文的图示与示例代码，并翻译说明）

### `'static` Future 问题与替代方案

（保留示例、FuturesUnordered、LocalSet、JoinSet 的解释和练习）

> **关键要点 — 当 Tokio 不适合时**
> - `FuturesUnordered` 在当前任务中并发运行 futures，无需 `'static`
> - `LocalSet` 允许 `!Send` futures 在单线程执行器上运行
> - `JoinSet` 提供任务管理（但仍需 `'static + Send`）
> - 库应该依赖 `std::future::Future` 与 `futures`，而不是直接依赖 `tokio`

> **参见：** [第 8 章 — Tokio 深入](ch08-tokio-deep-dive.md)，[第 11 章 — Streams](ch11-streams-and-asynciterator.md)

***
